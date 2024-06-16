# HackerNickName

## About 

his challenge is a web challenge from the last international ctf organized by [AKASEC](https://akasec.club/) 

##

 - Once you open the website you found a form that ask you to enter your first name last name and the your fav category : <img src="https://github.com/youssef-badaoui/MY_writeups/blob/main/Web/first.png">
 - We fill the form and intercept the request : <img src="https://github.com/youssef-badaoui/MY_writeups/blob/main/Web/2.png">
 - Now let's check how the backend handel this request :
   ```java
   @PostMapping(consumes="application/json")
    public void post(@RequestBody @Valid Hacker hacker, HttpServletResponse response) {
        hacker.setNickName(nicknameService.getNickName());
        String token = jwtUtil.generateToken(hacker.getInfo());
        Cookie cookie = new Cookie("jwt", token);
        cookie.setHttpOnly(true);
        cookie.setPath("/");
        response.addCookie(cookie);
    }```
   

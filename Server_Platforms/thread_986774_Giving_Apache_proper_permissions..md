---
title: "Giving Apache proper permissions."
date: 2008-11-18
forum: Server Platforms
---

### Post by darkphaux on 2008-11-18
Alright I am running Apache2 just fine, I have even set up FTP access. All is good. So then I go and install SQUID proxy service (with authentication). My only logical thought was to make a website so that people could create a user name and password to the proxy. So I wrote a python script to test:
```

import os

def main():
    username = "test"
    password = "test"
    os.system("htpasswd -b /etc/squid/passwd '%s' '%s'" % (username.replace("'", ""), password.replace("'", "")))

if __name__ == '__main__': main()

```
 Now I placed the .py file in my /usr/lib/cgi-bin/ folder. My only problem now is that I am unable to execute it from the website. 

I would always get a 500 Internal server error. I tracked through my error log and determined that it was a permissions problem, and that the Apache user (www-data) does not have correct permissions. I tried changing the permissions of the cgi-bin to 755 and still no luck. Am I even on the right track? How can I give Apache the permissions it needs to execute commands. 

p.s. I am aware of the security risks of doing this. This site will never go wide scale and is only used more as a boredom busting project. 

-Thank you

---

### Post by darkphaux on 2008-11-19
Anyone?

---

### Post by HighCommander540 on 2008-11-19
I have actually found that for some reason Apache is really picky on what it needs to run as well as the other applications that are complied with it such as the CGI or PHP.

I have found that Apache basiclly needs full acess to the file for it to like it. Exact reasons I don't know, but I know that when I make my /var/www/ 0777 everything seems to work perfectly.

I don't know what the issue is, but try that. I know that isn't the greatest for security. But the only people that are even going to be able to edit or view it are the ones that you are already giving access to your server on. It is a big security hole, but it might be the only way.

---

### Post by darkphaux on 2008-11-19
Actually I just gave my /usr/lib/cgi-bin 777 permissions. That solved that but now I am having another problem. I need the proper headers for my python file to work. Anyone know them? I beleive it is just standard in/ standard out headers.

---


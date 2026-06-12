---
title: "Configuring Apparmor"
date: 2009-07-23
forum: Security
---

### Post by Victor43 on 2009-07-23
Can anyone tell me how to go about configuring Firefox in Apparmor ? I want only Firefox for now to access the internet and no other applications.   I followed the link here [http://ubuntuforums.org/showthread.php?t=812907](http://ubuntuforums.org/showthread.php?t=812907) but still cannot get it to work ? Another words how do I know that FF has been enabled by Apparmor ?  I ran autodep firefox from the terminal window and then I then proceeded to open and then close Firefox. I then tried running sudo logprofile and get command not found error. I am not sure what I am doing wrong.... please....help  Victor

---

### Post by rookcifer on 2009-07-23
You have to make a profile for Firefox.  All profiles are stored in /etc/apparmor.d.  There is an AppArmor sticky at the top of this forum that covers all of this.

---

### Post by bodhi.zazen on 2009-07-23
There are a number of aa profiles here : [http://bodhizazen.net/aa-profiles](http://bodhizazen.net/aa-profiles)

---

### Post by Victor43 on 2009-07-23
Thanks to all replies. I'll give the link you buys mentioned a try. Will post back if I run into any issues. 
 
Victor

---

### Post by Victor43 on 2009-07-23
Can anyone tell me why am I getting the following error(s): Thanks.  ```
Create New User?  (Y)es / [(N)o] Username: victor Password: xxxxxxx  Save Configuration?   [(Y)es] / (N)o  Login failure  Please check username and password and try again. RPC::XML::Client::send_request: HTTP server error: Not Found
```

---

### Post by bodhi.zazen on 2009-07-23
I suspect you should say no to that question, but what did you do to get that error message ?

---

### Post by Victor43 on 2009-07-23
> **bodhi.zazen said:**
> I suspect you should say no to that question, but what did you do to get that error message ?

 What I did I selected Yes to create a profile name. Then gave it a user name and then a password. It then asked for an email address then I got the above error. Please see the following log of the question that was asked of me. *Sorry* could not figure how to insert new line character.     Create New User?  (Y)es / [(N)o] y Username: victor Password: 12345678 Email Addr: [EMAIL="xxxx@hotmail.com"]xxxx@hotmail.com[/EMAIL]  Save Configuration?  [(Y)es] / (N)on  y  Login Error  RPC::XML::Client::send_request: HTTP server error: Not Found

---

### Post by Victor43 on 2009-07-23
I am also getting the following errors all the same in the log using the following command &quot;tail -F /var/log/messages&quot; which is being sent to the terminal window. Is this error because of I could not create a profile name ?       Jul 23 18:59:23 P3B-F kernel: [13623.445656] type=1502 audit(1248389963.290:37980): operation=inode_rename requested_mask= w denied_mask=w::fsuid=1000 name=/home/vicster43/.mozilla/firefox/sg8ivzal.default/sessionstore.js pid=6705 profile=null-complain-profile

---

### Post by bodhi.zazen on 2009-07-23
try answering no to create new user.

apparmor has some kind of central repository built into it, which is a good idea, but there are no profiles so just say no ;)

---


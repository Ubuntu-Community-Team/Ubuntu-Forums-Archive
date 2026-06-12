---
title: "apparmor transmission help 10.04"
date: 2010-05-28
forum: Security
---

### Post by karmicgaz on 2010-05-28
Firstly I have read and always refer back to the introduction to apparmor sticky. But when I use genprof to make a profile for transmission the program will no longer run. When I start it I get an error box on screen with all characters boxed and unreadable except the error symbol so I don't even know why.

---

### Post by bodhi.zazen on 2010-05-28
You need to read the logs to see what access is denied, and allow that access.

If you like, here is a link to my profiles, including transmission

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/)

---

### Post by karmicgaz on 2010-05-28
Thankyou,I haven't looked at the logs as transmission doesn't even start! But I will persevere, delete profile and start again. Thanks for your profile as a reference point.

---

### Post by Jive Turkey on 2010-05-28
You don't need to delete the profile every time, you need to edit and reload it.  
Start transmission, wait for it to fail, then check the log to see what apparmor blocked, update the profile to allow whatever it blocked, lather rinse, repeat, until all of the features you need work and it can do what it needs to do, and hopefully nothing else.

---

### Post by bodhi.zazen on 2010-05-28
> **karmicgaz said:**
> I haven't looked at the logs as transmission doesn't even start! 

That is the problem then, you need to watch the logs.

When I am debugging a profile I keep a dedicated terminal open 

```
tail -F /var/log/messages
```

---

### Post by karmicgaz on 2010-05-29
Thanks, I understand more now. Lather, rinse, repeat. Hee hee!
Will work through it tomorrow. Cheers.:)

---


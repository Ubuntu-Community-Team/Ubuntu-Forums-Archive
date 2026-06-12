---
title: "Help me shutdown this server so I can get some sleep"
date: 2011-09-23
forum: Server Platforms
---

### Post by BEEDO on 2011-09-23
This is a dumb question, but I am new to commandline. I thought I remembered how to shutdown but my command didn't work. The line: Try `shutdown --help' for more information. Because that showed info that helped me shutdown successfully last time. So* foolishly* I typed:

 `shutdown --help'

and got:

> 

and put:

>shutdown --help
>delete `shutdown --help'
>

So now I don't know what I'm doing, only that it is wrong.

Please help. Thanks.

---

### Post by spynappels on 2011-09-23
type a semi-colon (;) and enter to get back to the command prompt and then ```
sudo shutdown -P now
```
That should shut and power down your server.

---

### Post by BEEDO on 2011-09-23
I typed the semicolon

>;    

and 'enter'ed and wound up back where I started!?

>;
>

then,

>;
>;
>;
>


now what?

---

### Post by philipballew on 2011-09-23
```
sudo shutdown -h now
```

---

### Post by chathuras on 2011-09-23
press ctrl + c twice

---

### Post by spynappels on 2011-09-23
> **chathuras said:**
> press ctrl + c twice

and then do the ```
sudo shutdown -P now
```

the -P flag shuts down the power as well.

---

### Post by BEEDO on 2011-09-23
Thank you for the help. I work at this every evening. I have a long ways to go!

---


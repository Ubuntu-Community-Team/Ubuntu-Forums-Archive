---
title: "Install LAMP Server by Tasksel Help"
date: 2008-10-29
forum: Server Platforms
---

### Post by mltriebe on 2008-10-29
I recently tried to install LAMP Server through Tasksel but it removed A LOT of required files in the process.  As a result I had to completely reinstall Kubuntu.  My questions are as follows:

1. Did I do something wrong when I typed in Terminal:  Sudo Tasksel, then selected LAMP to be installed?

2. Would this command be any better, sudo tasksel install lamp-server, or will the result be the same?

3. Is there a better way to get the LAMP Server up and running?

I am still fairly new to Kubuntu so please be specific with any instructions.  I would ultimately like to run my website on a localhost for troubleshooting before going live with it.

Thanks, Mike

---

### Post by cariboo on 2008-10-29
There shouldn't be any files removed as the Lamp server has nothing to do with a gui.

> 1. Did I do something wrong when I typed in Terminal: Sudo Tasksel, then selected LAMP to be installed?

2. Would this command be any better, sudo tasksel install lamp-server, or will the result be the same?

The result will be the same.

```
3. Is there a better way to get the LAMP Server up and running?
```

You might be better off doing the server installation first, then adding the Kubuntu Desktop after you have set the server up.

Here is a server setup guide, it is a little more then you wanted, but you don't have to install the parts you don't need:

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

Jim

---

### Post by lifestream on 2008-10-30
+1 for the above poster's idea.
I have actually just done this myself, and couldn't be happier.

Installed the server, then installed a VERY minimal xfce desktop (could be whatever you want) by doing ```
sudo aptitude install xubuntu-desktop --without-recommendations
```


Then I just installed gedit, a terminal and a web browser. All good to go for a testing server!

---

### Post by mltriebe on 2008-11-01
Thanks, I got busy and then forgot about this thread.  Sounds like more than I want to do at this time since I need Windoze yet for Quickbooks anyway and I already have a server set up there.  

Mike

---

### Post by mltriebe on 2008-11-07
Just tried the command and it worked:

sudo tasksel install lamp-server

Mike

---


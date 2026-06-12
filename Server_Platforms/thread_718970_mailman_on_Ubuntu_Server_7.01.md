---
title: "mailman on Ubuntu Server 7.01"
date: 2008-03-08
forum: Server Platforms
---

### Post by hardwarecompugeek on 2008-03-08
hello, I am trying to install mailman on Ubuntu server (7.01), and I am having some difficulties getting it running.

OK, so I installed mailman with
```
sudo apt-get install mailman
```
And it did it's thing, then it said that I needed to create a site-list. I followed the on screen instructions, and it told me to type ```
newlist mailman
``` and then to follow the on screen instructions that followed. Well, that didn't happen, instead;

> 
Traceback (most recent call last);
     File "/usr/sbin/newlist", line 261, in <module>
          main()
     File "/usr/sbin/newlist", line 131, in main
          os.setgid(gid)
OSError: [Errno 1] Operation not permitted



Any help is appreciated in advance.
:confused::confused::confused:

---

### Post by Mr. C. on 2008-03-09
You are not root, and your user does not have permission to create new lists.  You must perform these commands as a user with sufficient permissions.  The on screen instructions assume you know this.

Try preceding your commands with **sudo**.

---

### Post by hardwarecompugeek on 2008-04-01
I am on the last steps getting this stupid thing installed, here is my next problem.

> Make sure the installation directory is set to group mailman (or whatever you're going to specify with --with-groupname) and has the setgid bit set3. You probably also want to guarantee that this directory is readable and executable by everyone. For example, these shell commands will accomplish this:

    % cd $prefix
    % chgrp mailman .
    % chmod a+rx,g+ws .

You are now ready to configure and install the Mailman software. --The Directions

When I get to the chmod a+rx, g+ws . I get chmod: invalid mode: 'a+rx,'  how would I fix this?

And what does the % sign mean? I typed in once, but I got an error saying that it doesn't know what it is, or the command is invalid. So I stopped typing it in, and now everything works alright? (Just curious)

---

### Post by Mr. C. on 2008-04-01
> **hardwarecompugeek said:**
> 
When I get to the chmod a+rx, g+ws . I get chmod: invalid mode: 'a+rx,'  how would I fix this?

Make sure there is no space between the comma and the g+ws.
> **hardwarecompugeek said:**
> 
And what does the % sign mean? I typed in once, but I got an error saying that it doesn't know what it is, or the command is invalid. So I stopped typing it in, and now everything works alright? (Just curious)
The % char is the **csh **default prompt.  It is there just to indicate that you enter your commands at the shell command line; but you don't enter %.

---

### Post by hardwarecompugeek on 2008-04-03
could someone please send me a virus and totally destroy my windows machine so that I can finally learn how to use Linux!!!!!!!!!!!!!!!!!!!!

I'm sooo sorry for being such a Linux noob, I can't believe that I am asking such noobish questions!!!!!



Now I have to install putty on my iPod, which I have no problems building applications for by the way.
:guitar:

---


---
title: "Funny Font Terminal Command Response"
date: 2007-10-07
forum: The Cafe
---

### Post by shuukazedojo on 2007-10-07
So, I'm very new at this Ubuntu thing despite having had it on the computer for some 6 months or so now. There are still some basics I don't understand being a recovering Windoze user like the concept of root and permissions. 

Apparently, you have to change the permissions to add fonts?!? Still not sure. If anyone has a good article or ten on these things, I would really appreciate the enlightenment. 

Anyway, just thought I'd share a screenshot of my frustration. I had some help in the background shouting the commands...hence the mount command. I just love the response. 

Now, if I only I could find this root... :D

---

### Post by koenn on 2007-10-07
> **shuukazedojo said:**
> 
Apparently, you have to change the permissions to add fonts?!? Still not sure. If anyone has a good article or ten on these things, I would really appreciate the enlightenment. 

the sudo command means "execute [what follows] as root". You only write paths there, not commands, so that's not going to work

'copy'  doesn't exist in linux, it's 'cp'

The only way I ever installed fonts was with a package manager. 
Maybe someone in the help forum / beginners forum can help you further. 

And ... they have rules here about posting images with adult content.

---

### Post by Kingsley on 2007-10-07
"sudo /usr/share/fonts" 

lmao that looks so idiotic when I look at it now but I probably did the same kind of thing when I was new to Linux.

---

### Post by shuukazedojo on 2007-10-09
> **Kingsley said:**
> "sudo /usr/share/fonts" 

lmao that looks so idiotic when I look at it now but I probably did the same kind of thing when I was new to Linux.

As much as I appreciate the arrogance, I would appreciate direction more. Thanks for the support.

---

### Post by picpak on 2007-10-09
What? You need to be root to add fonts? Heck, you don't even need the terminal.

Open up your home folder and create a new folder called **.fonts**. Hit Ctrl+H to see hidden files, go to the .fonts folder and put your fonts in there. Done.

---

### Post by shuukazedojo on 2007-10-09
Now that was the BEST information I've received yet!!!! THANK YOU!

Do you have a source for more user friendly tips like these? I would like to understand Ubuntu better so I can use it and eventually teach others how to use it. Maybe one day it will take over the world. But I digress. Any good source for the basics?


*Sorry about the non-family friendly graphic. If I get some time, I'll edit it and repost. *

---

### Post by picpak on 2007-10-09
I'm not sure about sources. It's just one of those things that you pick up on the forums that you wish you'd had known before.

Here's another good one: instead of always typing the folder path, just drag and drop the folder into the terminal.

---


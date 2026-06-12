---
title: "StarCraft 2 Retail CD: &quot;Error: Access Denied&quot;"
date: 2010-07-27
forum: Wine
---

### Post by TreadLight on 2010-07-27
I try to open the Installer.exe contained from within the StarCraft II: Wings of Liberty disc with Wine 1.2, but I get a window with the title "Error" and content as "Access Denied".

I think it is because I am not the owner of the file, and thus don't have proper permissions. It shows "501 - user #501" as the owner of the file. How can I change that?

Or is there another way?

Thanks in advance.

---

### Post by asdfoo on 2010-07-27
[http://wiki.winehq.org/FAQ#head-f3515230c198befe0279d32c448d9c8da63be66f](http://wiki.winehq.org/FAQ#head-f3515230c198befe0279d32c448d9c8da63be66f)

---

### Post by wcradar on 2010-07-27
I had a small problem, I can run the program but it doesnt let me click play&#8230;.

---

### Post by Remasis on 2010-07-27
> **asdfoo said:**
> [http://wiki.winehq.org/FAQ#head-f3515230c198befe0279d32c448d9c8da63be66f](http://wiki.winehq.org/FAQ#head-f3515230c198befe0279d32c448d9c8da63be66f)

Thanks for the condescending reply but it was no help at all.

I'm having the same issue. Trying to find a workaround to get the permissions correct when you mount the thing but so far no dice... Anyone have any ideas?

edit: Mounting with "mount -t udf -o ro,unhide,uid=1000 /dev/sr0 /media/cdrom"  fixes the permission issue but I am unable to run the installer via wine.

---

### Post by Pikestaff on 2010-07-27
I got it working by copying the entire CD over to a folder on my Desktop, then changing the permissions on the folder and installing it from there.  A bit of a roundabout solution but it works.

---

### Post by medv4380 on 2010-07-27
Same issue.  I'm not sure what's caused the problem but the only way I've found to work around it is here [http://www.clockworkhare.com/2010/07/penguin-post-how-to-install-starcraft-2-on-linuxwine-if-you-get-weird-permissions-issues.html](http://www.clockworkhare.com/2010/07/penguin-post-how-to-install-starcraft-2-on-linuxwine-if-you-get-weird-permissions-issues.html)

---

### Post by Pikestaff on 2010-07-27
> **medv4380 said:**
> Same issue.  I'm not sure what's caused the problem but the only way I've found to work around it is here [http://www.clockworkhare.com/2010/07/penguin-post-how-to-install-starcraft-2-on-linuxwine-if-you-get-weird-permissions-issues.html](http://www.clockworkhare.com/2010/07/penguin-post-how-to-install-starcraft-2-on-linuxwine-if-you-get-weird-permissions-issues.html)

Heh.  Thanks for linking my blog post. ;)  Glad to be of service!

---

### Post by theparticle010 on 2010-07-28
Thanks! I was going to run starcraft 2 in windows like I did fallout 3 'till I got something to work on linux only to find out that you needed internet to install and my wireless card doesn't work well with windows, so, well after finding this and upgrading wine it seems to be working out quite well for me today, moved Fallout 3 To linux, and Now Starcraft 2!

---

### Post by moonbooter on 2011-06-21
Hey dude I had the same error when re-installing sc2. Heres what I did, oh and im using XP btw. Boot up in safe mode but allow internet acess. I did this by typing msconfig into run. Once booted up in safe mode I could install sc2 without the previous error. Once it is done and updated (takes ages btw) just restart your computer out of safe mode and it should work.
 
Additional: If you boot up in safe mode without allowing internet acess you can still install but will require an authentication key which i couldnt find. So deffo allow internet when in safe mode to make everything easier.
 
Hope this helps mate, this error was driving me crazy. Gl hf.

---


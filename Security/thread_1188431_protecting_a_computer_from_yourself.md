---
title: "protecting a computer from yourself?"
date: 2009-06-15
forum: Security
---

### Post by Bense on 2009-06-15
I know, I know, I know.  It's a bit crazy.  But allow me to explain.  

I am a 3rd year mechanical engineering student that's very very ADD.  For the past 10 years computers and the internet have been my absolute biggest distraction.  For the past 2 years I have been trying to avoid working with a computer in front of me, but I have now gotten to the point where I NEED to have a computer to do my homework.

The goal here is to take my laptop into the library and lockout every distractable feature from myself.  This laptop already has windows7 on it and I have a spare 30GB partition.

Here's what I was thinking last night.

* Base install of linux
* Very minimalistic window manager (openbox or something)
* matlab
* maple
* pdf viewer
* openoffice 
* kernel compiled with ntfs, wireless, and ethernet drivers as modules.  
* every other distractable program removed!

Then I would take the modules and remove them from the harddrive and place them on a flashdrive that I left in my bedroom.  I could install lilo on the harddrives MBR with no option other than linux boot.   On that same flashdrive I could install grub with options to boot into windows.  This would give myself sort of a "key" requirement to the ADD enticing functions of my shiny toy.

However I later realized that I could just get a little crazy and edit /etc/lilo.conf then /sbin/lilo and get to it.

So my question for you guys is, do you know of any way that I can get something like this accomplished?  It's kind of tricky because previously the goal that I had was to always find a workaround to bypass these kind of things.  So in a way I need to figure out a way to defeat myself.  Or set this computer up so that nothing can be done without a certain tool.

I know that one can easily say "just learn to control yourself" and I realize this.  I have **_struggled**_ with getting distracted my entire life.  I will be struggling enough with just the content of my courses, so it seems that the best option is to set that aside and lock myself out hahaha.

My last resort is to take an older notebook that I have.  Physically remove the wireless card and only install linux on it, and remove the modules for wireless/ethernet from it.  It just sucks because these older notebooks are larger/heavier/not as portable.  And the reason that I got this new notebook (asus n81vg) was because it's a lot lighter and more portable.

:P

---

### Post by lykwydchykyn on 2009-06-15
Not sure about the booting issues offhand, but it seems like the best approach is to give the admin/root password to a friend or family member and not know it yourself.  That will prevent you from adding any software or making any major changes to the system yourself.  Also set up your linux with a separate /home directory with the "noexec" flag in /etc/fstab so that you can't run software from your home directory.

As long as you have internet access and access to root (directly or via sudo), you can't really lock yourself out.

---

### Post by Bense on 2009-06-15
I GOT IT.   All I gotta do is move the /sbin/lilo binary to the key drive as well.

No option to boot to windows, no drivers for wireless networking, no drivers for wired networking, no drivers for ntfs, no program to modify the MBR.  

No video games, no internet, no music library to screw with, no movies, no distractions.    This could actually work.


The onlyyyy other thing that I **might** consider now is to enable wireless for shoutcast radio, but then I would have to remove all webbrowsers, all irc clients, all ssh clients, all ftp clients, all IM clients, telnet clients, rsync, terminal services clients, apt-get, and email clients, wget, and anything else.  Then get a simple player (xmms or something) that I can stick a few radio station urls in.  

I can see this actually working, and I could keep a "key" in my room/car so that when I got done getting lots of work done in the library, I could grab my "key" and go straight to a lan party.  :P

---

### Post by lisati on 2009-06-15
The only sure-fire way I know of protecting a computer is to disconnect it from absolutely everything and putting it somewhere physically safe. Dismantling it, putting it in a hole in the ground, and filling the hole with freshly mixed concrete is optional.

---

### Post by gnoob on 2009-06-25
its slightly funny that you bought a laptop with 1gb dedicated graphics and you are going to lock it up. but i guess with the key you could then just plug it in and go game when you dont need to work...

---


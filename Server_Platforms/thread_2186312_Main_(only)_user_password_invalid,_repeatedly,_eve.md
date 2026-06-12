---
title: "Main (only) user password invalid, repeatedly, even after reset"
date: 2013-11-06
forum: Server Platforms
---

### Post by whitelouis on 2013-11-06
Hey guys! 

I've searched and found threads close to my problem, but none seem to go quite far enough to solve the problem...stay with me, this may get a little long winded, but I'd like to be thorough to hopefully help you help me more easily. :)

I'm running Ubuntu 12.04 LTS server edition, with the default Ubuntu/gnome GUI. It's primary use is as a personal development server for PHP, MySQL, Javascript, Java, and JQuery. It's also got tons of disk space, so it's my home file server for multimedia as well.

Yesterday I was attempting to update Samba from 3.6.3 to 4.1 (stable) via tarball downloaded from Samba's site. I removed and purged smbd, then went through with creating a directory - /usr/local/src - to extract the Samba 4.1 tarball into, proceeded to chown that directory, ./configure 'd, then used 'make' to install. All seemed to go well, and finally I used checkinstall. This led through a few options, the last of which I don't remember the words of exactly, but my interpretation was that there were excess files from the intsall which were nolonger necessary, and would I like to view them? Default was no, but wondering what they were, I hit y and perused through them pretty quickly, when I got to the end it simply said (END), but wouldn't let me do anything else with the terminal window.

I tried a variety of things, but none seemed to do anything, so eventually (against my better judgement) I just closed the terminal, despite the warning that there was still a process running in it.

I did a quick ls /etc/init.d to see if the new version of Samba was running, but found it not listed, so I rebooted, momentarily falling back to my years of Windows experience.

When I tried to log back in, I was greeted with repeated "Invalid password" notices upon entering the same password I've had on the machine since I installed, and have never had an issue with. Guest account worked (obviously) but that's not much help.

Thinking perhaps the password had been altered through something I did, I rebooted into recovery mode, dropped to the shell as root, used 'mount -o rw,remount /' and then 'passwd [user]', entered a new password twice, was told it was successful, exited, resumed normal bootup, got to the log on screen and had the same issue.

Thinking maybe the GUI was to blame, I used CTRL+ALT+F1 to get out of it and tried to log in that way, but every time I enter the username and password, it just flashes back to the same "username" prompt. No errors, nothing, just as if I hadn't ever typed anything. I even changed the password to "a" just to test it, and entered it 30 or so times out of stubborn frustration, to no avail.

The only other thread I found with a near identical issue resulted from an over-liberal use of chown on the /usr directory, but after checking ownership/permissions with 'ls -l /usr' and 'ls -l /usr/local' via the recovery root shell, it seems all directories in both are root:root except the /usr/local/src directory I created, which is [user]:root.

Sorry that was a lot of info, but that's the last thing I had done before the issue arose. I'm pretty sure those are all the commands I used, after installing - via 'apt-get install' - a bunch of dependencies. 

If it comes to it, having to re-install isn't the end of the world, as I don't have any really important files on the physical drive Ubuntu is on, and can use the live-disc first to move any files that I want to keep, but it'd be great to use this as a learning experience and figure out how to fix it!

Thanks in advance for your help!

---

### Post by cariboo on 2013-11-07
I'm not sure what you expect after you have entered your password, but at the prompt in a terminal it is normal not to see any thing except your username after you've logged in.

---

### Post by whitelouis on 2013-11-07
Sorry, I guess I didn't quite specify. When I log in with the correct password, it doesn't show my username, it just clears the screen back to only showing OS info at the top, and the "Server login:" prompt as if I haven't entered anything. 

If I try the wrong password, it tells me login incorrect, and gives another server login: prompt, but if, after that, I give it the right password, it just clears everything, back to square 1...

Per a suggestion in the general help section, I tried connecting via wired ethernet, entering recovery mode, then enabling networking and selecting fix broken packages, to no avail. It updated/fixed empathy and some other things I didn't recognize, but none of them were things I had done anything with, ever, to my knowledge...

Thanks for any ideas you've got.

---


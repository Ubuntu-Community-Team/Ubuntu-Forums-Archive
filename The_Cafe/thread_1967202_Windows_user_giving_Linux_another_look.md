---
title: "Windows user giving Linux another look"
date: 2012-04-27
forum: The Cafe
---

### Post by Cecil on 2012-04-27
So, it seems that every so often I get curious and decide to look into Linux. This time I first decided to try it out in a virtual machine on my desktop (which I will keep Windows on, as I play a lot of games). Well, after that I went over to my laptop, backed up my data and wiped Windows from it. My laptop is now running Ubuntu 12.04 and runs a lot better than it did with Windows 7. So, let me list the things I have enjoyed about Ubuntu Linux;

1: Boot-up times. Seriously, it loads a lot faster than Windows 7 did, and once on the desktop programs load quite fast.

2: Great for school/office use and web browsing. I'm currently attending college over the internet, and Ubuntu came with most of the programs I needed to get my work done. Only downside isn't even Ubuntu's fault; there's a program called LabSim that I use for my computer classes, and after failing to get WINE to work with it, decided to install Windows XP into a virtual machine to run it.

3: Ubuntu Software Center. Having a central place to browse and download programs I may want/need is very nice. Then there's the fact that once I find a program I want, I just have to click the Install button and it sets up automatically along with any dependencies it may need. No multiple clicks through an installation program like in Windows.

There are a few things I do like Windows 7 over Ubuntu, like the way I can mouse-over a program in the taskbar and see a thumbnail of it, but it's not exactly a vital function. Also, I am still learning my way around Ubuntu (if anyone can tell me if there's anything like Windows' Local Security Policy in Ubuntu, I'd appreciate it), but overall, for what I use my laptop for, the Linux alternatives work great, and it runs faster than Windows did. As for my desktop, however, I will keep Windows 7 on it. There's just too much I do, gaming being the major activity, on my desktop to switch. For my laptop, however, Ubuntu just became its main OS.

---

### Post by GameX2 on 2012-04-27
Welcome to Ubuntu, mate. ;)

For some reasons, I love to help newbies, they remind me of how much I was amazed when I first saw Ubuntu (Just in october, in fact ^^") . ;P
About the thumbnails, do you know about Compiz, yet?  It manage all the amazing visual effects that Ubuntu have!  To install it, go to the software center, and type "Compiz"; then install "CompizConfig", and launch it like any normal applications.

Be aware that Compiz is powerful, and it can break your desktop.  I manage to recover it myself when it happen, but just be careful.  To add the thumbnails:

- In the Extras category, click on the button "Windows previews";
- Then just tick the box "Activate Windows Previews".  Done!  (For some reasons, the thumbnails won't show up if you tweaked the dock to have it on the bottom of the screen)

And you haven't paid a cent.. ;)

Enjoy Ubuntu ! :D

---

### Post by Cecil on 2012-04-27
> **GameX2 said:**
> Welcome to Ubuntu, mate. ;)

For some reasons, I love to help newbies, they remind me of how much I was amazed when I first saw Ubuntu (Just in october, in fact ^^") . ;P
About the thumbnails, do you know about Compiz, yet?  It manage all the amazing visual effects that Ubuntu have!  To install it, go to the software center, and type "Compiz"; then install "CompizConfig", and launch it like any normal applications.

Be aware that Compiz is powerful, and it can break your desktop.  I manage to recover it myself when it happen, but just be careful.  To add the thumbnails:

- In the Extras category, click on the button "Windows previews";
- Then just tick the box "Activate Windows Previews".  Done!  (For some reasons, the thumbnails won't show up if you tweaked the dock to have it on the bottom of the screen)

And you haven't paid a cent.. ;)

Enjoy Ubuntu ! :D
Oh, cool! I'll give that a try, then, thanks! Also, any idea if there's a "Local Security Policy" equivalent in Ubuntu? I like to fine-tune security settings.

---

### Post by Version Dependency on 2012-04-27
> **Cecil said:**
> 3: Ubuntu Software Center. Having a central place to browse and download programs I may want/need is very nice. Then there's the fact that once I find a program I want, I just have to click the Install button and it sets up automatically along with any dependencies it may need. No multiple clicks through an installation program like in Windows.

The Software Center has most things you would ever want but probably not all.  There are plenty of apps that aren't in the official repos (especially the non-open-source variety).  A couple that come to mind are Skype and Opera...but both of those (and many others you may want) are still dead simple to install.  Go to their website and click the download links (they know you run Ubuntu) and a click or two later you're done.

---

### Post by Penguinnerd on 2012-04-27
> **Cecil said:**
> Also, any idea if there's a "Local Security Policy" equivalent in Ubuntu? I like to fine-tune security settings.

Not as such. You can do individual things to enhance security, like running a firewall and installing noscript in firefox to diable un-needed (and possibly malicious) scripts. There are lots of other things, like making sure that remote desktop stuff is disabled, making sure you have a good password, etc.

But: There's a fine line between usability and security. It's already quite secure, although I'm a little more paranoid.

For more detailed info on locking-down your system, look at threads in the security section.

---

### Post by GameX2 on 2012-04-27
> **Version Dependency said:**
> The Software Center has most things you would ever want but probably not all.  There are plenty of apps that aren't in the official repos (especially the non-open-source variety).  A couple that come to mind are Skype and Opera...but both of those (and many others you may want) are still dead simple to install.  Go to their website and click the download links (they know you run Ubuntu) and a click or two later you're done.

Yes, these are .DEB files, the easiest to install. ;)
Just open them, and they redirect you to a page of the software center.

---

### Post by Cecil on 2012-04-27
> **Penguinnerd said:**
> Not as such. You can do individual things to enhance security, like running a firewall and installing noscript in firefox to diable un-needed (and possibly malicious) scripts. There are lots of other things, like making sure that remote desktop stuff is disabled, making sure you have a good password, etc.

But: There's a fine line between usability and security. It's already quite secure, although I'm a little more paranoid.

For more detailed info on locking-down your system, look at threads in the security section.

Ah well, that's fine. I'll take a look in the security section, then. Thanks. Also yeah, not everything is in the software center, and it's pretty easy to download and double-click on a .deb file to install software.

I installed CompizConfig and enabled Windows Previews, it's nice having that little feature again. I'll make sure to take care using it, I don't want to break my desktop. Overall though, I'm pretty happy with how well Ubuntu is running on my laptop, it's come a long ways since I tinkered with Linux in the past.

---

### Post by GameX2 on 2012-04-27
> **Penguinnerd said:**
> Not as such. You can do individual things to enhance security, like running a firewall and installing noscript in firefox to diable un-needed (and possibly malicious) scripts. There are lots of other things, like making sure that remote desktop stuff is disabled, making sure you have a good password, etc.

But: There's a fine line between usability and security. It's already quite secure, although I'm a little more paranoid.

For more detailed info on locking-down your system, look at threads in the security section.

Also, I would recommend you to protect your system against the forkbombs; in a terminal (CTRL-ALT-T), type this, which will open a file:

```
gksudo gedit /etc/security/limits.conf
```

Right before # End of file add this line:

```
*              hard    nproc           100
```

This limit the number of process the system will handle (here, the limit is 100 processes).  You might want to change 100 to 200 or 250.  Save the file, then test the command:

```
ulimit -u
```

It should show the number you've put in the previous file.  Reboot, that's all!


EDIT: Well, if you break your desktop, it's recoverable (not so hard, depending on the situation), ask here and we'll help! ;)

Just a tip: if Ubuntu freeze, or is your desktop is unusable - like you can't logout, type CTRL-ALT-PrintScreen-K.  This will force quit the session (kill).  Don't worry, it keep all your settings and doesn't reset anything.  Seriously useful when freezes randomly happen.

---

### Post by nothingspecial on 2012-04-27
I'm not sure that is strictly necessary.

The best protection against forkbombs is to only allow shh access with keys and to not type/paste random things you see on the internet into your terminal without first understanding what they will do.

---

### Post by Cecil on 2012-04-28
> **nothingspecial said:**
> I'm not sure that is strictly necessary.

The best protection against forkbombs is to only allow shh access with keys and to not type/paste random things you see on the internet into your terminal without first understanding what they will do.

Good advice for anything, really; know what you're doing before you do it. On that note, I just found a list of 7 things not to do in Linux that I'm going to read over so I don't go making any dumb mistakes in the future.

---

### Post by Version Dependency on 2012-04-28
> **Cecil said:**
>  I just found a list of 7 things not to do in Linux that I'm going to read over so I don't go making any dumb mistakes in the future.

#1  No one in Nigeria is going to give you some huge payout to help them retrieve "unclaimed funds."

:D

---

### Post by Bandit on 2012-04-28
Install a Firewall, Software Center has some good ones. Dont surf as root or copy and paste everything you see on the internet into the terminal. Do that and your safer then most banks.

---

### Post by craig10x on 2012-04-28
Linux has a lot of built in security by it's very nature...it's a LOT different then windows...

The only thing i do when i install ubuntu (security wise) is add a simple firewall program you will find in the software center called "gufw" and turn it on (i don't even make any fancy settings)...

What that does is make you "stealth"...if you go to a test site like "shields up" and do the test...once i turn on gufw i notice it shows that i am invisible...;)

Virus scanners and other malware programs aren't really needed on here...

---


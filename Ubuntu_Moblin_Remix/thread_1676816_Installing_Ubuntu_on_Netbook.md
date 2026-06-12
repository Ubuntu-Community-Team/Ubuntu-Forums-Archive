---
title: "Installing Ubuntu on Netbook"
date: 2011-01-27
forum: Ubuntu Moblin Remix
---

### Post by Delta.13.0 on 2011-01-27
Hi all,

I'm trying to install Ubuntu on my Netbook, using a USB flash drive.  It has been stuck on the 'loading' screen for about 3 hours now.  What's going on, is that normal?  Shall I leave it on over night?  What do you advise, please?

Thank you.

Delta

---

### Post by ajgreeny on 2011-01-27
Not at all normal, and I doubt there is any point in leaving it any longer.

What do you mean by the "loading screen"?  Have you got to the gnome desktop of the live CD/USB yet or is it still trying to boot to that?

What netbook is it, with what hardware?

Did you check the iso md5sum, and then then install medium (USB) from the first menu when you boot?

---

### Post by Delta.13.0 on 2011-01-28
I don't have the desktop.  It was stuck on the Ubuntu screen with the 5 dots, which looked like it was doing something, but hasn't!  No menu appeared.

Anyway, now I've just pressed the F1 key once (randomly, don't know what made me do that!) and there's a long message like this:

Begin: Configuring power management... ...done.
Begin: Enabling detection of crashes... ...done.
Begin: Disabling unnecessary KDE services... ...done.
Begin: Fixing language selector... ...

Obviously the message is longer than that, but I just wrote the last few lines.  It's stuck on the fixing language selector.  Does anyone know what that means?  Shall I start again?

MSI Wind U100 Netbook with Intel® Atom™ N270 1.6GHz processor.

Thanks, ajgreeny.

---

### Post by sikander3786 on 2011-01-28
Welcome to the forums :-)

Did you check the MD5SUM of your downloaded image as suggested above by **ajgreeny**?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the sums match, burn a new USB and this time, use unetbootin.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Keep us posted ;-)

---

### Post by Delta.13.0 on 2011-01-28
Sorry, what do they mean by the download directory?

My iso file is on the desktop.

Thank you!

---

### Post by sikander3786 on 2011-01-28
Then your download directory is

```
cd ~/Desktop
```

---

### Post by ruegore on 2011-01-28
A "directory" is like a folder. They're the same thing, but most folks know them as "folders". The Desktop is just another folder among your file system. It just serves a special purpose.

I have Ubuntu Maverick Meerkat on my MSI Wind U123, and it works very well. Your netbook isn't that different from mine.

I'm assuming you're trying to use the latest Live CD iso on your USB stick, so if that's the case, try again and when you see a tiny icon at the bottom/center of your screen that looks like a keyboard, press the ESC key. Soon it should load up a menu of 5 options to boot from, but it'll quickly populate most of the screen with a list of languages. Just hit ENTER to select the default language "English" to get back to the boot menu.

From here, you can select "Install Ubuntu" which should be the second option. It'll then boot into a custom live environment and begin the step-by-step install process. If that doesn't happen at all, you could try using the "Alternative" ISO disc instead of the "Live" ISO. The "Alternative" uses a text-based install screen and usually works much better.

Good luck!

---

### Post by ajgreeny on 2011-01-28
And my netbook is a re-badged MSI Wind U100, with same specs, and also can say that everything works great with both 10.04 and 10.10, though I use gnome, not the UNE desktop.

---

### Post by Delta.13.0 on 2011-01-28
I've tried all your suggestions; now it's just a matter of waiting.  It seems stuck on the Ubuntu screen, though.  Is there supposed to be some indication as to how the install is going, or should I just wait?  Any idea how long it will take?

Thank you everyone. :)

Edit: I am trying the "Alternative" option now!

---

### Post by ajgreeny on 2011-01-28
It normally takes 15 -20 minutes getting to the ubuntu live desktop, hitting the Install icon  and getting to the reboot so I think there maybe a fault with your iso file.

If the iso file is on your main ubuntu desktop use the command from terminal ```
md5sum Desktop/*filename*.iso
```Use the full filename of the iso by typing the first few letters and hitting Tab for auto-completion.  Now compare the alphanumeric output of that command with the one you find at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes") for that iso.  I think you probably have **ubuntu-10.10-netbook-i386.iso**  which should have the md5sum **6877bf8d673b87ba9500b0ff879091d0 **    
 
If it is the same you should be OK, if it is different even by one digit, it will not work.

---

### Post by Delta.13.0 on 2011-01-28
Thanks for your reply, **ajgreeny**.

I am doing it the Alternative way now.  

It seems to be stuck on "Partitions formatting" - it's been 33% for a long time now.  Does that mean there could be something wrong with the hard drive?

Thanks for your patience with me.  I am very new to this.

(By the way, I am using my Dell laptop (running Windows 7) to post on this forum, so can I still check md5sum from here?
Also, I tried using **ubuntu-10.10-netbook-i386.iso** and **ubuntu-10.10-alternate-i386.iso**)

---

### Post by ajgreeny on 2011-01-29
Yes, you can, but I do not have windows on my machines, so will have to let you search for how to do it on the [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) page.

---

### Post by ruegore on 2011-01-30
Have you got passed the partitioner yet?

---

### Post by Delta.13.0 on 2011-01-30
Thanks for your replies.  It was still stuck at 33%.  There was no error message, but the message I saw was:

Creating ext4 file system for / in partition #1 of SCSI1 (0, 0, 0) (sda)...

I've tried 10.4 and 10.10 now, both Live and Alternative.  I don't understand how it can be failing so many times (am I really that bad? :P)  Should I try an earlier version?

---


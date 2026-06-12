---
title: "Improvements to make to Ubuntu 8.10"
date: 2009-03-23
forum: Ubuntu Brainstorm
---

### Post by markosjal on 2009-03-23
I have switched some machines to Ubuntu now, and I see the following annoyances in Gnome. I post them here only for suggestions for improvements, not to be flamed for how stupid I am for not finding the option that I want to activate and could not find. It is a pretty sure bet that if I have not found such options by now, they are not easy enough to find!

I am a computer user that has used DOS , Windows, MacOS, Amiga so I make these suggestions in order that someone can run with them to improve the Ubuntu project.

Gnome File Browser; Always show a COPYABLE full path in title bar (or at least the option)

Gnome File Browser;Gnome File Browser; Make added shares in loweer part of Left pane remain through a reboot

Gnome File Browser;Option to allow image previews on SMB shares. I know this will slow things down by default but is necessary for those with photos on network shares (should be settable on a per folder basis)

When A NTFS disk is mounted, space may be inaccurately reported as the Disk space on the mount point and not the actual disk! If the system disk (containing mount point)  runs low on space you ca no longer write files to the NTFS disk


SMB shares seem to "disconnect" when unused for a while . Attempting to open them a second time yields expected result

SMB shares are not accessible from the Save dialogue of all programs. IN fact when a Network share is added in file browser it still may not appear in program save dialogues.


INstaller: need the option to NOT INSTALL GRUB on an existing windows partition, in the event a user is selecting start up disk in BIOS!

Any time the installer TOUCHES an existing partition such as whgen installing GRUB onto the windows partition, user should be CLEARLY warned.

Mark

---

### Post by smartboyathome on 2009-03-23
> **markosjal said:**
> Gnome File Browser;Gnome File Browser; Make added shares in loweer part of Left pane remain through a reboot

This requires putting an entry into your /etc/fstab. [Here is an article to help you.]("http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/")

> **markosjal said:**
> Gnome File Browser;Option to allow image previews on SMB shares. I know this will slow things down by default but is necessary for those with photos on network shares (should be settable on a per folder basis)

This should be reported to the GNOME Bug tracker.

> **markosjal said:**
> When A NTFS disk is mounted, space may be inaccurately reported as the Disk space on the mount point and not the actual disk! If the system disk (containing mount point)  runs low on space you ca no longer write files to the NTFS disk

Again, I think this is a bug and should be reported.

> **markosjal said:**
> SMB shares seem to "disconnect" when unused for a while . Attempting to open them a second time yields expected result

This might have to do with the server, not the client.

> **markosjal said:**
> SMB shares are not accessible from the Save dialogue of all programs. IN fact when a Network share is added in file browser it still may not appear in program save dialogues.

This is where the /etc/fstab entry will help, as it tells you where to find it. ;)

> **markosjal said:**
> INstaller: need the option to NOT INSTALL GRUB on an existing windows partition, in the event a user is selecting start up disk in BIOS!

This is there, if in an inconvenient place. At the very end of the installer, right before you actually click install, click advanced, and then enter the hard drive position (hd0 is the master hard drive, hd1 is the slave hard drive).

> **markosjal said:**
> Any time the installer TOUCHES an existing partition such as when installing GRUB onto the windows partition, user should be CLEARLY warned.

I think it is already clearly defined that it will do that stuff. Most people don't use multiple hard drives like this.

---

### Post by markosjal on 2009-03-23
I think the post I made states that SOME  of these may already be present but difficult to find or understand. I did not ask for a review of my opinions. 

Especially as related to the install on a second hard disk and the GRUB menu installed on primar, THIS IS NOT CLEAR, NOR IS ONE ADVISED!

---

### Post by koenbeek on 2009-03-23
I think the following site is the best way to suggest improvements to ubuntu (not bugfixes)

[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

any idea can be voted up or down and if it is popular enough, it'll probably be worked on sooner rather than later

---

### Post by markosjal on 2009-03-25
I found the web site pretty unfriendly, and I believe that any such developers should look here!

I should not have to separatre out my ideas, nor should I have to say I have "hardware available for testing" because I USE my computers , not play with them

I also am opposed to having multiple l,ogins and sites for a single product

---

### Post by Merk42 on 2009-03-26
> **markosjal said:**
> I found the web site pretty unfriendly

The big button on the right saying "submit your idea" was unfriendly?

> **markosjal said:**
> I believe that any such developers should look here!

Well a lot of your comments had to do with GNOME, which is used in a lot more distributions than just Ubuntu.  That's like making a comment about Firefox in a Windows forum.

> **markosjal said:**
> I should not have to separatre out my ideas, nor should I have to say I have "hardware available for testing" because I USE my computers , not play with them

But again, you're talking about different programs, most of which Ubuntu doesn't actually make.
If you bought a computer with Windows loaded onto it, it would come with a lot of software not made by Microsoft, and as such, it wouldn't make sense to make comments about the software in a Windows/Microsoft forum.

> **markosjal said:**
> I also am opposed to having multiple l,ogins and sites for a single product

I'm pretty sure you can use the same login, you'll just have to make a new account with the same info.

I do agree with what you say though, but that's a problem with the websites, not the software of course.

---

### Post by Penguin Guy on 2009-03-27
When linking to a partition that is not already mounted, Ubuntu brings up an error - when it should automatically mount the partition then follow the link.

---

### Post by smartboyathome on 2009-03-27
> **Penguin Guy said:**
> When linking to a partition that is not already mounted, Ubuntu brings up an error - when it should automatically mount the partition then follow the link.

The hard part about that is that several partitions can be mounted to the same location. For example, /media/disk1 can have one partition mounted, then it gets unmounted and the next partition will be mounted there. So, unless you label the partitions or add them to FSTAB, it would be hard to do this.

---

### Post by BGFG on 2009-03-28
If it's enhancements you are suggesting, no need for all the exclamation marks and rude tone.

---


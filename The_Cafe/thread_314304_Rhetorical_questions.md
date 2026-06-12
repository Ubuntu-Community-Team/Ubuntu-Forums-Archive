---
title: "Rhetorical questions"
date: 2006-12-07
forum: The Cafe
---

### Post by lukkystarr on 2006-12-07
Ok, I'm not new to Ubuntu, though I don't use it on a regular basis.  I decided last night to set it up though for use on a regular basis.  Why?  Because the others I'd tried - Fedora and Suse - would not give me access to my SATA drives out of the box.  I've given up on wireless for now, I have a TrueMobile which nobody seems to want to write a good driver for.  

So, I decided to redo everything and put Ubuntu on the main computer for good.  I did this last night, with new partitions on hda.  Installation was fine (I've done it thousands of times) everything was great, with access to all my ntfs and SATA drives.  I did all the updates, then logged off and went to bed.  

This morning there were still 18 updates.  I did those as well, because I (used to) trust the Linux people.  Then I start configuring things the way I like them.  Things were going ok until I needed some jpeg files for backgrounds on everyone's login.  They are on an ntfs partition.  I start looking.  After a few minutes I realized I no longer had access automatically to those drives.  I have two IDE and two SATA drives, and I had access only to the linux file system.  I had it last night - then after the updates, I don't.

Why, why, why, would I not want access to these drives on my computers at home?  Has someone been talking to Mr Ballmer?  Is this why Bill has been out of the spotlight, so he can schmooz some people that handle other distros besides suse?  

I know, it's easy to fix.  But read the subject - rhetorical questions.  Why should I have to 'fix' something I didn't want 'broken'?  I LIKE having access to all my stuff.  Who wouldn't?

---

### Post by jdong on 2006-12-07
Welcome to UbuntuForums,

The first thing you need to do is adjust your attitude. We don't try to design Ubuntu to purposely make it harder for you to access your data, so don't try to make it seem that way.

Then, if you still need help diagnosing your NTFS issue, post /etc/fstab and output of the 'mount' command.

---

### Post by lukkystarr on 2006-12-07
No, I do not have to change my attitude.  I like it, thank you very much.  And no, I don't have to post output so someone can help me, I very much believe in RTFM, and I am quite capable of fixing my own fstab file. 

This is not to say that I don't appreciate everything that everyone in open source is doing to help it along.  Oh, I most certainly do.  Everyone that contributes is a helluva lot smarter than I am, so I have done my small part for the last ten years by learning as much as I can in the little time I can spare, and not whining about how it is not as easy as windows.  I can edit my own configuration files to some degree.  I can't write the applications, but I can learn to use what others create.  I RTFM, I try everything that is available, and tout Linux to anyone that will listen, because the people that actually write this stuff want people to use it. 

The whole point here, with Linux, is that the user has control of the machine.  It does make sense, after all, to any reasonable person.  That is why I found it so hard to believe that things had changed on my computer.  These are updates, does it make any sense to anyone that an UPDATE should change such a basic configuration file?  I don't know exactly what changed it, and I don't care.  I know it wasn't me, because I made sure it was the way I wanted it after installation.  And it was easy to fix, the entries I wanted were commented out, so I deleted some '#'s.  No big deal for me, but what is a new user supposed to do?  One day they have access to their drives, then they don't.  What are they supposed to think?  

I think it's great it is becoming easier to install and work with, but the concept is that the open source community, given enough time, can do things better than Microsoft does.  I think every user wants to have control of their machine at home, and one of the biggest reasons for using Linux is it gives the user more control if they are willing to work with it.  Something like this will turn people off in a hurry.  I remember way back when struggling with access to my windows partitions, but it is a helluva lot easier now.  This little detail is taking two steps back.

---

### Post by xpod on 2006-12-07
Someone sounds like they got sand in their f***y..

Fix it and stop whining
I certainly dont know what im doing like you may do:-k ... but this sounds like the hissy fits of someone with nothing better to do than whinge about things

Why dont you describe how you fixed whatever it was to help others?
Mabey you could write up some guides to HELP the people who are`nt as experienced as you in these matters:-? 

Just a thought instead of wasting all those precious beans:-#

---

### Post by jdong on 2006-12-07
Ok, at point I don't think this thread has any hope of being productive. You don't appear to be in need or desire of any assistance on this issue.

What you experienced is clearly some kind of bug because as you noted yourself, updates aren't supposed to disable previously working functionality. You could've taken this as an opportunity to help the Ubuntu distribution by providing some debugging information so we can trace down exactly what caused this undesired behavior. Instead, you decided to use this  as a chance to make sardonic remarks about Ubuntu and its developer community.

At this point I'm closing this thread.

---


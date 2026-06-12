---
title: "chown -R 'wrong user' / ... oops resetting original file system permissions"
date: 2008-11-09
forum: Security
---

### Post by linuxlover4444 on 2008-11-09
So last night I could not empty my trash can because the items in the trash could not be permanently deleted by my user account.  So I ran the ol

chown -R 'wrong user' / 

The command actually ran.  Soon, I emptied by trash but rebooted and fall all kinds of weirdness.  I figured out what I had done and decided on my path to fix.  I rebooted into the system root console from GRUB and did a chown -R root /.  All reset... and for the most part my system is operational again.

I still have some issues left.  No. 1 I have to manually start my Internet connection everytime I login as a non root user.  I can't get to the users-admin or services-admin applets under Gnome.

When I try to run these apps I get an error about setuid, SO I have not totally brought my system back to the same level of life as it was on my original install.

Does anyone out their in the Linux cloud know of a specification by Ubuntu or other group that would

1. Contain the original file system permissions on a vanilla installation?
2. Maybe even have a list of commands on what to run (chown, chgrp, etc.) to get your permissions back to normal?

Thanks,
LinuxLover4444

---

### Post by linuxlover4444 on 2008-11-09
How bout a reply to my own original post for additional information.  To recover my machine after the chown to my lesser privileged personal account I 

chown to root on all files.

After I rebooted into Ubuntu, I received errors when logging into my less privileged user account due to all of my home files being owned by root.  I then rebooted into the Grub recovery root console and chown on my home directory to my lesser priviledged user account.

So what is messed up now?

- My screen saver comes on but I can no longer unlock my system with my user account password.. weird! : - )

- I can not open any of the gnome system admin tools (services, user and groups) logged in as either root OR my lesser privileged user account.

- I have to run /etc/init.d/networking stop then start with my lesser privileged account or my network won't work!  It works fine in root!  hehe.. in a sick way, my machine is much more secure since I have to manually start networking under root now!  haha

.............................

One thing that catches me as odd is I can chown the entire system but I can't find a spec on how to chown back, or "restore" my file system permissions.  Theoretically a specification would exist that would recommend the default settings for all aspects of my file system.  Does that exist somewhere?

This has been an excellent exercise in getting down and dirty into Linux internals so the pain is worth it, but I am still lacking some information.

You can't tell me the Mr. Shuttleworth's team does not know where the file system permission and group security spec is.

I used default Ubuntu settings on the original setup and only have my one user account.  Nothing advanced, just like most.

---

### Post by cariboo on 2008-11-09
The problem more than likely lies in your home directory have you changed the ownership of the files in /home/<user> to yourself?

> You can't tell me the Mr. Shuttleworth's team does not know where the file system permission and group security spec is.

Canonical and Ubuntu have nothing to do with setting file ownership and permissions. You should look here for the Linux file system specifrication:

[http://www.linuxfoundation.org/en/Specifications](http://www.linuxfoundation.org/en/Specifications)

Remember Ubuntu is a **Linux** distribution, if you can find a specific solution in the forums, try a general Linux search.

Jim

---

### Post by linuxlover4444 on 2008-11-09
Thank you for your attempt to help me sir.  Yes, I already reset permissions on my home directory.  I figured that out after logging in and seeing issues with files needing to be owned by my personal account on my home.

I am also looking for information on the delta between the core linux file system permissions and Mr. Shuttleworth's specific distribution.  Where a distribution leaves the linux core alone and where they change it per distribution would be a powerful document.  Business adoption of technology might not be so afraid of choosing one distribution over another if they sold Linux in that manner!  They would have something to hold in hand that would provide people like me with a way to fix problems which would also provide those businesses with a way to fix problems.  

Thank you for your reply.

---

### Post by cariboo on 2008-11-10
I don't think you are going to get an answer to your question here. I currently have 340592 files on my / and /home partitions it would be pretty hard to catalog the ownership and permissions of each and every file. you may have a better chance of getting an answer here:

[https://answers.launchpad.net/](https://answers.launchpad.net/)

You will have to register to ask your question.

Jim

---

### Post by hyper_ch on 2008-11-10
Chowning everything is not good... a lot of things maybe returned to their original ownerships but not everything. I recommend a full re-install of your system.

---

### Post by The Cog on 2008-11-10
I was going to say I think you need to reinstall, but hyper_ch has beaten me to it. 

That's the only way you are going to restore all the correct ownerships, and some of them are quite important (and not necessarily what you would expect). You can use recovery mode to read your home directory first and replace it after the reinstall. Your home directory should all be your own so that's not going to be a problem.

---

### Post by amac777 on 2008-11-11
I just wanted to say that in my opinion, you made two mistakes with the command "chown -R 'wrong user' /".

The first mistake was the 'wrong user' as you said you already realized.

But the second mistake (and more fundamental mistake) is you told it to recursively go through your entire file system starting at root directory /. Instead, at most, you should have specified only the trash folder that you were concerned with, and better yet, just the particular file you couldn't delete.

However, that said, since you did not preface that above faulty command with "sudo", you probably didn't have the rights to actually change all the files on your system and do any real damage. The command probably only changed the ownership on the files in your home directory and possible a couple others like tmp. You probably also got an error message of some sort telling you something like operation not permitted.

But then you "rebooted into the system root console from GRUB and did a chown -R root /"...... WOOPS. This command was, in my opinion, what probably caused the real damage to your system because you booted into root console so now you actually had the power to change everything on your system. What you should have done here to recover was just change the ownership on the files in your home directory back to the correct user but leave all the other system files alone.

Unfortunately, I agree with the other posters. I don't think there is any reliable way to recover from this situation. You probably need to back up your files and then reinstall from scratch.

---

### Post by x3roconf on 2008-11-11
> **hyper_ch said:**
> chowning everything is not good... A lot of things maybe returned to their original ownerships but not everything. I recommend a full re-install of your system.

+1

---

### Post by martiendejong on 2009-06-12
I am having the same problem, and trying to fix it. 
I think the only thing I need to fix now is the .dmrc file.
I set all the permissions right, except for the wrong owner.
Is there a way to switch it back when using a Live CD or booting from another partition?

When I try to do 'chown .dmrc martien' it says unrecognized user name.
What can I do to get the user back?

Best regards,
Martien

---

### Post by unutbu on 2009-06-12
Try drs305's excellent guide on how to fix .dmrc:
[http://ubuntuforums.org/showthread.php?p=6208727](http://ubuntuforums.org/showthread.php?p=6208727)

---

### Post by panurgebr on 2012-11-11
Found at ubuntugeek a way to help me fix the whole system:
sudo dpkg-reconfigure -phigh -a

[http://www.ubuntugeek.com/ubuntu-tip-reinstall-ubuntu-automatically.html](http://www.ubuntugeek.com/ubuntu-tip-reinstall-ubuntu-automatically.html)

Maybe isnt the most trustfull be at least got things back again. I think the command can be improved

---

### Post by cariboo on 2012-11-11
A three year old thread, is a three year old thread. A lot has changed in the last three years. This thread is closed.

---


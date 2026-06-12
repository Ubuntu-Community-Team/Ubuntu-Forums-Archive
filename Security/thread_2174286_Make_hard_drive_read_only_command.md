---
title: "Make hard drive read only command"
date: 2013-09-13
forum: Security
---

### Post by HardTrickySecurity on 2013-09-13
Hi

I try to make my hard drive read only, but it said it was busy. Then I force it to unmount with a command, but I was inside Lubuntu, if I unmount my hard drive well obviously is going to crash the whole thing.

How can I do this. Is there a work around? I just need to be able to mount it as read only without chrashing my OS Lubuntu. And been able to put it back to write and read again. So I can switch beteween this 2 options using commands on the terminal.

Ive been recently attacked by a hacker this way. And also using the hard disk encryption option. He dodge the security soon or later. Just live cd has work for me.

Thanks

---

### Post by sudodus on 2013-09-13
Welcome to the Ubuntu Forums :-)

If you boot from an Ubuntu live CD, it will be possible to do 'anything' with the hard disk drive. You can unmount it, and nobody can 
read/write. And you can mount it read-only, unmount it again and mount it read-write when you want to write. See the details in the manual page of mount

```
 man mount
```

```
       -o, --options opts
              Options  are  specified  with a -o flag followed by a comma separated string of options.
              For example:

                     mount LABEL=mydisk -o noatime,nouser

              For more details, see FILESYSTEM INDEPENDENT MOUNT OPTIONS and FILESYSTEM SPECIFIC MOUNT
              OPTIONS sections.
...

       remount
              Attempt to remount an already-mounted filesystem.  This is commonly used to  change  the
              mount flags for a filesystem, especially to make a readonly filesystem writable. It does
              not change device or mount point.

              The remount functionality follows the standard way how  the  mount  command  works  with
              options  from fstab. It means the mount command doesn't read fstab (or mtab) only when a
              device and dir are fully specified.

              mount -o remount,rw /dev/foo /dir

              After this call all old mount options are replaced and arbitrary  stuff  from  fstab  is
              ignored,  except  the  loop=  option which is internally generated and maintained by the
              mount command.

              mount -o remount,rw  /dir

              After this call mount reads fstab (or mtab) and merges these options with  options  from
              command line ( -o ).

       ro     Mount the filesystem read-only.

       rw     Mount the filesystem read-write.

```

---

### Post by HardTrickySecurity on 2013-09-13
1) Ok I was able to mount and unmount the hard disk in the live cd, with the proper commands. But I dont want to use the hard drive just store or save documents. I want to be able to install programs and security lubuntu updates, etc. The thing is how can I connect the live cd and the hard disk in order to do that. If I try to install a program in the harddrive well obviously is not going to work, the hard drive is empty and has no Lubuntu directiories files required in order to install software or programs.

2) Now the other approach or way I am trying is:

Not using a live cd, and boot from the hard drive with the OS installed, but I dont know if there is an option to make read only the hard drive without umount.

Is there is such an option? Make the hard drive read only without umount for this escenario? Or is just not possible?

I cant umount, if I do that the OS crash it freezes.

---

### Post by sudodus on 2013-09-14
> **BGfF7rD said:**
> 1) Ok I was able to mount and unmount the hard disk in the live cd, with the proper commands. But I dont want to use the hard drive just store or save documents. I want to be able to install programs and security lubuntu updates, etc. The thing is how can I connect the live cd and the hard disk in order to do that. If I try to install a program in the harddrive well obviously is not going to work, the hard drive is empty and has no Lubuntu directiories files required in order to install software or programs.

If you do that, you will be as vulnerable to attacks as if you have a regular installed system. It is called a persistent live system, and is also more error prone (it can break easily and you cannot update the kernel).
> 
2) Now the other approach or way I am trying is:

Not using a live cd, and boot from the hard drive with the OS installed, but I dont know if there is an option to make read only the hard drive without umount.

Is there is such an option? Make the hard drive read only without umount for this escenario? Or is just not possible?

I cant umount, if I do that the OS crash it freezes.

A normal installed system uses the drive for many write operations, and cannot have a read-only root file system. You have to choose, either have an operating system, that is read-only (you can only change it temporarily (in the ram-drive), but after shutdown the changes are wiped, or have a system that can write to disk. And then there is always a risk, that some malware will enter into it.

What kind of threat are you afraid of? Attacks via the internet connection or attacks at home or at the office, when someone else will get physical control of the computer?

You can also get tips from this link [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by HardTrickySecurity on 2013-09-14
> **sudodus said:**
> If you do that, you will be as vulnerable to attacks as if you have a regular installed system. It is called a persistent live system, and is also more error prone (it can break easily and you cannot update the kernel).


A normal installed system uses the drive for many write operations, and cannot have a read-only root file system. You have to choose, either have an operating system, that is read-only (you can only change it temporarily (in the ram-drive), but after shutdown the changes are wiped, or have a system that can write to disk. And then there is always a risk, that some malware will enter into it.

What kind of threat are you afraid of? Attacks via the internet connection or attacks at home or at the office, when someone else will get physical control of the computer?

You can also get tips from this link [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)





Ohh I see. Now its all clear. Ok so I will have to figure out a workaround for this one, for my specific case. 

Well my case is little bit complicated, it all start when I was making buisness with the wrong people on internet. Now this people, want to bother me because I was able to make a negative impact regarding to money and profits to this company, wich by the way its a fraud. So believe or not they hired a hacker or hackers to be 24 hours, so they bother me and not allow me to work in my computer normally and basically stalking me.

What kind of threat I am afraid of? Well the attack they did was to my hard drive, with Lubuntu OS installed. I dont know if they were able to get my root password wich it was a strong one. But they where able to move, erase, create files, open windows, crash programs, bring internet connection, mess and block my bookmarks and crash the hole OS, take full control of USB and files inside, and they were able to see my desktop and what I was doing in real life time. So I use the encryption OS hard drive option for more security, that you can choose when you install Lubuntu with cd iso, with a strong pharaprase. The first time I did this, it took them around 1 week to finally dodge the securiy. The next attempts they where able to do it in a couple of hours or less. So I suppose I will have to buy one of those hard drives with encryption incorporated in hardware. To see if they can dodge that one.

Another thing is that everytime the hacker does the attack to my OS, in a live cd, I get a pop up message warning from Lubuntu. That it sais basically that write is not allowed. That is a read only system. So I know that when this happens its the hacker trying to get away with it. But it cant because is a read only system. I am going to put a screenshot of the pop up message, just let me check how to do that.

---

### Post by HardTrickySecurity on 2013-09-14
Lets me see if I did it right, I use the attachments option.

---

### Post by HardTrickySecurity on 2013-09-14
The screenshot above, was using Lubuntu 13.04 live cd. See how the hacker cant make the attack succesfull. To tell you the true I dont know what kind of attack is this, if is a rootkit, or just from terminal, or what tool is using. But it defenetly needs to be able to write in hard drive.

---

### Post by sudodus on 2013-09-14
Screenshots are made by pressing the PrintScreen key or alt + PrintScreen for the selected window. The program doing the job is ***scrot***.

The screenshot is saved in your home directory, the file name starts with the time (year, month, day, clock), and you can edit or convert it to be suitable to attach to a post.

-o-

So the attack is always via the internet.

I think you can apply several protective layers around your computer.

- How can your internet service provider help you? Ask them for help.

- What kind of firewall have you got? Can you close all incoming ports? Use wired internet (avoid wifi).

- Can you use a proxy? [http://www.wikihow.com/Be-Online-Anonymously](http://www.wikihow.com/Be-Online-Anonymously)

- Are you running a web page (a server), or are you only running a normal desktop computer connected to the internet?

- Are you doing business via the internet and need the show your identity? That makes it harder. In that case, you need professional advice.

You can use different systems for different tasks. Use a live system without persistence for web activities, that are sensitive, maybe using a proxy and encrypted tunneling for example https.

Do what you can do without any connection to the internet. Connect to the internet only when you really need it, for short periods. Do not leave the connection on, when you are not using it. And do not leave the computer on, when you do not need it.

Take backups frequently, so that you can restore your system to a state, that is not damaged by an attacker. Store at least one backup in another house if possible.

---

### Post by sudodus on 2013-09-14
> **BGfF7rD said:**
> The screenshot above, was using Lubuntu 13.04 live cd. See how the hacker cant make the attack succesfull. To tell you the true I dont know what kind of attack is this, if is a rootkit, or just from terminal, or what tool is using. But it defenetly needs to be able to write in hard drive.

I'm not sure it is an attack at all.*** /dev/fd0*** is the floppy drive. There might be an entry for it in /etc/fstab, and the computer tries to find it, and finally gives up and complains with that message.

---

### Post by cariboo on 2013-09-14
There is another case, where the *can't /dev/fd0 error* may come up. The floopy module hasn't been loaded by default for several releases, so if there is a floppy drive connected to the system, the error may come up. 

As far as mounting the hard rive read only goes, if you do this your are still going to run into problems, as the OS needs to have write access to the hard drive for at least /tmp and /var. I'd suggest you would be much better off reading the stickies at the top of the page, to secure your system, and still make it usable.

---

### Post by HardTrickySecurity on 2013-09-22
Yes I know it looks like it is the floppy. But I dont have connect to my pc a floppy, and I turn it off in my mobo bios. I dont use a floppy.

Apparently the hacker has to do some kind of mount device procedure, the floppy or the usb or the hard drive in order to make the attack succesfull. Like I said I am not a pro on black hat offensive techniques so I dont know the name for this attack.

I have an intermidiate level at white hat defense techniques I suppose.

The hacker does something like the next video, but not phisically from my home, in my case the hacker does it through internet.

[http://www.youtube.com/watch?v=n9Wbgy0DDMQ](http://www.youtube.com/watch?v=n9Wbgy0DDMQ)

The other thing is Ive been dealing with all the attacks this hacker has been doing to me. That when something fishy happends I know that is the hacker doing that. Is like recognising a pattern that is very obvious. 

I know this one is tricky. Cause you have to know when it is:

1) A false positive, legitime: A technical problem, internet drop down, a mistake from user, etc,etc,etc...

or

2) A hacker attack: It disgaise like if it is a technical problem to confuse (hacker), internet drop down (hacker), a mistake from user, etc,etc,etc...(hacker)

This 2 formats are very similar or identical, and sometimes the only way to recognising them, is doing a very deep study about the problem.

I am going to show 2 more screenshots of the attack. Just a minute...

---

### Post by HardTrickySecurity on 2013-09-22
I am trying to upload the next screenshot but the size is 1.3 MiB, and its not allowing me. I will have to figure it this one.

---

### Post by HardTrickySecurity on 2013-09-22
I called my ISP and they told me.

-They dont have a deparment specialized on security
-They dont have a deparment that provides linux support.
-We dont use a firewall between the internet and their users or customers to protect them.

No wonder, this is an easy one for a hacker that knows what he is doing.

Basically Lubuntu is doing magic for me in my case. Lubuntu sais he guys I know I can be very secure with some hardening and so on, but I need some hardware security help on this one.

Oh well, the situation gave me no other choice to make an investment on some hardware security (hardware firewall,hard disk SSD SED) This combined with Lubuntu or linux in general, and some hardening OS. Is going to give some hard time to this fool (hacker).

I am just missing the hardware VPN, but that will be for later. In the meantime software VPN

[URL="http://www.wwpi.com/index.php?option=com_content&id=2669&Itemid=44"]
http://www.wwpi.com/index.php?option=com_content&id=2669&Itemid=44[/URL]


Thanks for help guys

---

### Post by HardTrickySecurity on 2013-11-09
Grsecurity and PAX fix the problem and big time.

---


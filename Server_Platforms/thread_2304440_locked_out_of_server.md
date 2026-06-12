---
title: "locked out of server"
date: 2015-11-26
forum: Server Platforms
---

### Post by Sirport on 2015-11-26
I realise this may not be allowed but I have to ask.

Our IT person was informed that they were to be made redundant.
They didn't take this too well.
Long story short is that they have locked everyone out and I have been tasked with getting control back.

I need to get back into the server somehow and reset root/admin password (I think?) and take control back.
I have access to the physical computer so can reboot into a safe mode or similar?
I have a windows background,linux is not my forte and I have just over 12hrs to 'learn' how to do this.

Thanks

---

### Post by darkod on 2015-11-26
I don't know if it's allowed too, but I guess it is since you have physical access to the machine.

Something like this should help you: [http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password)

It has a quite detailed description... Even for a windows guy. :)

PS. I now realised the instructions assume you know the username of the first user created. If you do not, after you do the remount step, try something like:
```
cat /etc/passwd
```

That should list all users (including some system users) on the system. The first user created should have an id of 1000. Anyway, you should be able to check all usernames there...

---

### Post by Sirport on 2015-11-26
Thank you darkod

I will give that a good read and I'll also make USB a bootable version.

---

### Post by Sirport on 2015-11-27
Is it possible to tell which users have admin/root rights?

---

### Post by Lars Noodén on 2015-11-27
You can look at the contents of /etc/group to see who is in which group.  Then you can look at /etc/sudoers to see which extra permissions have been added to various users or groups.

---

### Post by matt_symes on 2015-11-27
Hi

> **Sirport said:**
> I realise this may not be allowed but I have to ask.

Our IT person was informed that they were to be made redundant.
They didn't take this too well.
Long story short is that they have locked everyone out and I have been tasked with getting control back.

I need to get back into the server somehow and reset root/admin password (I think?) and take control back.
I have access to the physical computer so can reboot into a safe mode or similar?
I have a windows background,linux is not my forte and I have just over 12hrs to 'learn' how to do this.

Thanks

There are some good replies but the replies are making some assumptions such as the sudo binary is still there.

Any good IT guy will know a whole bunch of ways to really make your life difficult and really lock everybody out.

The good thing is that you have physical access and want to boot from a CD/USB but has the old admin added a BIOS password ? a grub password ? You really need to find out what the state of the system is ?

Do you have full disc backups you can restore to ?

What kind of server is this ? I take it, it's not exposed to the Internet ? If so it maybe have a backdoor.

You want to consider this as if it does then all your hard work to fix it may be undone remotely. Does the motherboard have IPMI or vPro ?....

Just some food for thought...

Kind regards

---

### Post by Lars Noodén on 2015-11-27
> **matt_symes said:**
> 
Any good IT guy will know a whole bunch of ways to really make your life difficult and really lock everybody out

+1

matt writes what was also in the back of my mind when I wrote the reply above.  If you do find any back doors, I'd say do the reinstallation as soon as humanly possible.   And even if you don't, I'd move the machine towards the top of the list for a re-installation because once someone malicious has had root access you kind of have to consider the machine done for.

---

### Post by Sirport on 2015-11-27
My thoughts also.
Not sure how malicious they are going to be,it may just be a 'you need me' kind of a thing but who knows.

I also need to transfer/copy some files from a usb HDD to the main HDD,usb hdd is plugged into the pc.
Not familiar with putty and not totally sure of the file structure.

If I run my bootable usb version can I access the server from home and do a simple copy/paste or drag/drop?
Googling found midnight commander which looks like it could be just the ticket but it comes in various .tar.xxx formats and have no idea how to 'install' it haha

Thanks

---

### Post by Lars Noodén on 2015-11-27
midnight commander is in the repository as "mc"

---

### Post by darkod on 2015-11-27
In theory you should be able to copy files to it from live mode if you use the desktop live usb to boot into live mode.

The server hdd will not be in /home. When you open the file manager (called Nautilus by the way), on the left side it will list all detected hdds. The server hdd should be there. With Nautilus you can work with a GUI to help you copy files easily.

Note that you might need to copy as root to allow you to do it, but in such case the copied files on the destination might be owned by root and you will probably need to change their permissions depending on the setup so that other users can use them.

Also, in some cases, like when using software raid mdadm on the server, live mode might not see the disk automatically unless you do other needed steps.

So the first thing to do would be to boot the server in live mode and check if you can "see" the hdd. This assumes you want to use GUI to work.

You could also use the recovery mode mentioned in that article I linked for the password reset. That will give you command line access to the server without using any desktop cd/usb.

---

### Post by Sirport on 2015-11-27
I ran the live usb and had a quick lookaround and it seems relatively straight forward,this was on my own machine.
Can I use my live usb on my machine and use it to log in to the server and transfer files that way?

---

### Post by darkod on 2015-11-27
Yes and no. Assuming the server has no GUI interface and you can only log in using ssh session, you would still be stuck with working on the command line only. For that, you don't even need a second machine, do the recovery mode and the root shell on the server itself.

Also, for ssh session you will need a working user/pass. Did you manage to sort that out (the resetting)? Otherwise you can't open ssh session without a user.

---


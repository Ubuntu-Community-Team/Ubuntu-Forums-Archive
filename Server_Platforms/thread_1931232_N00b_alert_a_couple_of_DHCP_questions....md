---
title: "N00b alert: a couple of DHCP questions..."
date: 2012-02-25
forum: Server Platforms
---

### Post by iangarforth on 2012-02-25
Hi all,

I'm slowly and gently trying to convince my school to move towards a Ubuntu system.

My short term plan is to build a small and simple Ubuntu network.  The long-term goal is to get users' existing files to mount successfully so that they can see all their files.

In the first instance, I want to create a small and simple server, and it really will be a practice network - I'm not letting anyone go wild on anything yet...

I presume the regular Ubuntu server needs a static IP, and therefore I need to get my systems administrator to reserve me an IP from the current range, right?

I then create a few accounts that access this server.  In the first instance, I want them to be be able to access the Internet, save files to their space, and print.  I'm not worried about them getting access to their old files on the rest of the network yet.

Does Samba need a separate static IP, again excluded from the current 'whole network' DHCP?

---

### Post by roelforg on 2012-02-25
Samba shouldn't care about whether you use static/dhcp.
My server uses dhcp, but i set an override on my dhcp-server so that the server always gets the same ip.
I'd install the clients this way: THIN-CLIENTS!
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

The clients don't need a HD, they use a master image from the server.
Then make a nfs share containing all home directory's on the server,
and modify fstab of the master image to use the nfsshare as /home
and make a "misc" nfsshare for certain things i'll list.
Modify the fstab to mount that one on /opt/misc
/opt/misc could house shared configs

As linux saves all user-specific stuff in their homedir, only that dir has to be rwx for users, everything else is root-only.
The pc's will sync with the root image every boot.
Updates are easier too!
Just mount the image and use apt-get's options to use an alternate root-dir (the dir the image is mounted in that is), that way you can use apt-get to install/update stuff!
However, if you want to keep it easy, just go complete nfs [https://help.ubuntu.com/community/Installation/OnNFSDrive](https://help.ubuntu.com/community/Installation/OnNFSDrive)

---

### Post by iangarforth on 2012-02-25
Thanks very much for your answer.  It certainly gave me lots to think about, and I did a lot of reading around it to discover more.  In the end, though, I think my limiting factor is that my server just doesn't have that much grunt, so I think thin client is probably asking for trouble.

So the way I took your message, was suggesting that thin client was the way to go, but that in your last suggestion, you seemed to be saying that if I decided to keep it easy, to avoid thin client, and go Ubuntu/NFS.  Have I got that right?

That document detailing the NFS deployment seems like a bit of a monster.  Are you aware of any easier approaches?

---

### Post by iangarforth on 2012-02-25
By the way, in my 'client logs on and gets their old files mounted into their current machine' model, am I right in saying I don't need Samba?  I'd just do the whole job lot with NFS?

Or would I still need it for printing?

---

### Post by Jonathan L on 2012-02-25
Hi Ian

Great project for you.  I'd recommend you take it one step at a time: server, then NFS and/or Samba, then printing.

I wasn't entirely clear if you wanted just to make an Ubuntu server, or have Ubuntu workstations too.  While 
I agree wholeheartedly with Roelforg that you will get a lot of mileage out of  diskless clients (and I think you'll also be amazed about how much grunt is NOT  required on the server to support them for most ordinary  web/email type operations anyways.)

If you're using Ubuntu client machines for people to work on, you can easily do everything on the server with NFS.  If you want to support Windows clients you will probably find it better to use Samba on the server (yes, can do both).  If you've got Macintoshes they can use NFS or Samba, or you can install apple protocols too.

Printing: no, you don't need Samba for printing, you can use other things from ubuntu clients (and indeed Windows and Macintish clients).

So, if you'd clarify whether you want to have Ubuntu desktops for the people or not, and it will help get you the advice you need.

Specifically about IP addressing.  It's definitely best if you can get a static IP address for servers, but it doesn't much matter so long as it doesn't change very often.  From the point of view of learning how to set up Ubuntu servers, it's a very small part, and easily changed from DHCP to static at a later date.  (Edit /etc/network/interfaces)

Hope that's of some help.

Kind regards,
Jonathan.

---

### Post by iangarforth on 2012-02-25
Thank you so much for your thoughtful and considered reply, Jonathan.  

The situation will essentially be that over the Summer, our school network looks like it will be rebuilt/reconfigured.  That looks like leaving us with a bunch of 'legacy' laptops.

I have suggested to our top brass that I think Ubuntu is the way to go, for all kinds of reasons.  I also appreciate that right here, right now, that's probably too big a gamble for most.  So I've suggested I take 15 of the laptops and build a 'mini network' to show that it can be done, that it will run on older hardware fine, and as a 'proof of concept' to try and move us over to Ubuntu on a larger scale.

Originally, I planned to create workstations on the laptop on a generic log on - username = 'student', and if people wanted to save, then they could use Ubuntu One, or similar.  Now that seems like I'm missing a trick.  It seems entirely possible to build a Ubuntu server that serves 15 Ubuntu workstations, using the existing authentication (LDAP, with a bit of luck) that I can then use to mount folks files into the profile they're using.

I don't doubt this won't be easy.  But it something to have a go at, right?  I don't have a lot to lose :-)

Now - in at least the short to mid-term, it's likely this needs to co-exist with a Windows network.  There is an existing file server in school, and I guess the ideal scenario is that everything gets mounted to and from that, yes?  In that folks could be using either Ubuntu clients or Windows clients (and I doubt actually that I'd be able to get rid of the Windows clients altogether - there are likely to be some applications in school (eg: CAD/CAM, etc) that are just too committed to it).

So - client workstations connecting to a SAMBA server that mounts their work from and to an existing file server on the windows side?  My goodness, this is starting to sound complicated..!

---

### Post by roelforg on 2012-02-26
Yeah, i just tried to do this with some VM's.
Just do (as root on ubuntu server 11.10):
```

apt-get update
apt-get install -y debootstrap nfs-kernel-server apache2
mkdir -p /ubuntu
debootstrap --variant=minbase oneiric /ubuntu
echo "" >> /etc/exports
echo "/ubuntu *(rw,fsid=0,async,no_root_squash,no_subtree_check,insecure)" >> /etc/exports
/etc/init.d/nfs-kernel-server restart
cp /etc/sources.list /ubuntu/etc/sources.list
echo <HOSTNAME> > /ubuntu/etc/hostname
tar xf boot.tar -C /ubuntu/boot
chroot /ubuntu
mount /proc
passwd
umount /proc
exit

```Note: the commands between chroot and exit are to be entered manually! The passwd will set your root password.
If you pm me your email, i'll send you boot.tar (vmlinuz and initrd images)
Now you can start it with (qemu VM version:
```

qemu -m 128 -kernel /ubuntu/boot/vmlinuz-* -initrd /ubuntu/boot/initrd.img-* -append "root=/dev/nfs nfsroot=10.0.2.2:/ubuntu ip=dhcp rw"

```(the 10.0.2.2 is the ip qemu gives the host in the virtual network)
Once booted and logged in.
Use
```

apt-get update

```and install your favorite *buntu-desktop package to set the ubuntu/lubuntu/xubuntu/etc desktop

Note: i may have forgotten something

It's mostly from [https://help.ubuntu.com/community/Installation/OnNFSDrive](https://help.ubuntu.com/community/Installation/OnNFSDrive) but there are some errors in the article, which i corrected in this post.

If you provide the ip of the server i'll supply you with a gpxe (etherboot) image to boot over net via dhcp.

---

### Post by SeijiSensei on 2012-02-26
> **iangarforth said:**
> Now - in at least the short to mid-term, it's likely this needs to co-exist with a Windows network.

Does the Windows network authenticate users now, like with Active Directory?  If so, you could configure the Ubuntu server to authenticate against the Windows server with either LDAP or [pam_smb]("http://www.csn.ul.ie/~airlied/pam_smb/").  I've used the latter on a Linux mail server that authenticates its users against an AD server.

---

### Post by iangarforth on 2012-02-26
> **SeijiSensei said:**
> Does the Windows network authenticate users now, like with Active Directory?  If so, you could configure the Ubuntu server to authenticate against the Windows server with either LDAP or [pam_smb]("http://www.csn.ul.ie/~airlied/pam_smb/").  I've used the latter on a Linux mail server that authenticates its users against an AD server.

It does authenticate users, though I don't know if it is via Active Directory or not.  That will be my first job for Monday - finding out more about the Windows side of stuff.

Roelforg - thank you for that.  I'm still not exactly quite sure what it is - and the website page has an interesting and amusing convo at the beginning where the authors don't seem that sure themselves!

It's essentially a way of creating a thin client Ubuntu system from an NFS share, right?  So would the NFS share be the Ubuntu server?  Or the Windows File Server?

---

### Post by iangarforth on 2012-02-26
> **iangarforth said:**
> So would the NFS share be the Ubuntu server?  Or the Windows File Server?

No, the idea is that it's any old NFS server, isn't it?  And the idea of it is basically to create an Ubuntu thin client system?

---

### Post by roelforg on 2012-02-26
> **iangarforth said:**
> No, the idea is that it's any old NFS server, isn't it?  And the idea of it is basically to create an Ubuntu thin client system?
See my last post, it explains how.
As long as you have root access and a apache2 and nfs server, you're fine.

---

### Post by iangarforth on 2012-02-26
I think you're several stages ahead of me, Roelforg :-)  Remember I still haven't installed Ubuntu Server yet (though am happy with the CLI and have read around the subject).

Having said that, the more I think about it, the more I can see that thin client may suit my purposes perfectly.  As this is becoming another thread, I'm going to start a [new one]("http://ubuntuforums.org/showthread.php?p=11720125#post11720125"), if that's ok.  Thanks for everything so far, Roelforg and everyone else.  The plot thickens... :-)

---


---
title: "Do I need to use domain naming? Less than 10 users"
date: 2010-06-09
forum: Server Platforms
---

### Post by 1serveyou on 2010-06-09
Hi everyone, I finally have my ubuntu server up and running on the most part. I can connect to it with Mac and PC(haven't been able to with ubuntu desktop yet), but I'm having some trouble. 

The first thing, is I only need 5 or so users, and haven't been able to find a tutorial that uses restrictions without setting up a domain. This is for my house, and rather not set it up, as it makes it tough for when I go to work and go to another location(Unless there is an easy way to switch from dhcp and static as well as change from wireless and wired). 


I've tried using the Samba by Example 3, which seems to be the best at giving real life examples, but still running into problems when it comes to password protecting. Currently, I have it setup to ask for a login/password, but if you basically type anything in, it will accept it. I believe when I typed in a login/password with just numbers it denies me. I have no clue why it is doing this, and has been quite the pain. 

Any help or links would greatly be appreciated.

---

### Post by bodhi.zazen on 2010-06-09
I can not follow what you are asking and what you are wanting to do.

Do you need help with DNS ? Apache ? password protecting apache directories ? file sharing ? over a LAN ? over the internet ?

If you are needing DNS on a LAN you can either use /etc/hosts (you will need to update this file on each client) or look at dnsmasq

dnsmasq is light weight and very easy to configure. It will perform dhcp if neeedes and works well on a small LAN.

---

### Post by 1serveyou on 2010-06-09
Bodhi,

I apologize for that, as after I reread it, it is a bit confusing. I am having trouble with access to password protected directories using Samba. I did some more research and it looks like I can have certain folders password protected I want without setting a up domain. It makes it look a bit too easy, and I will feel bad for wasting people time if it does work tonight when I get home. This is the tutorial I will be testing tonight [http://samba.netfirms.com/sambconf.htm#smb](http://samba.netfirms.com/sambconf.htm#smb)

This is only going to be used locally for now, until I can get this all configured.

Also most of the tutorials I saw made you setup or already had setup a domain and did everything through that, so I thought that was the way it had to be done, but upon further search I found out that isn't the case. The reason I didn't want to setup a domain(I already have a workgroup) was that I figured it would make it tougher for me to connect my laptop to wireless/wired at work and other locations. When I had my laptop on a fixed IP because I was testing something on the server, I then brought it to work with the fixed IP still enabled and I couldn't connect to the internet(which makes sense as we don't use the same IPs). I rather make it smooth as possible when I'm connecting to different networks, as it can get annoying having to change your ip everytime you move to a different network. Again I apologizing for going off topic on my initial thread.

---

### Post by bodhi.zazen on 2010-06-09
Well, that I know of, you can not password protect a specific file or directory, you would use permissions on the server.

You can set a password for a samba mount. When you mount a samba share you need to provide a (samba) user name and password.

When you do this, on a Windows server, you use your windows log name and password.

When you do this on a Linux you set up a samba user. The samba user can have the same name as your user log in and even the same password, but it is set different.

It is a bit of a mess, I understand, but see this page :

[https://help.ubuntu.com/community/SettingUpSamba#File%20Sharing%20%28Basics%29]("https://help.ubuntu.com/community/SettingUpSamba#File%20Sharing%20%28Basics%29")

[FONT=Verdana]On the Server, use smbpassword to set up a samba user.

Then edit your smb.conf and set the global settings and use the general syntax for a private share.

[/FONT][FONT=Verdana][global]
        security = user
        encrypt passwords = true
        map to guest = bad user
        guest account = nobody[/FONT][FONT=Verdana]

[share_name]
[/FONT][FONT=Verdana]        comment = Private Share
        path = /path/to/share/point
        browseable = no
        read only = no[/FONT]See the wiki page for a more detailed explanation.

If you do not use a domain, you can mount it with

mount -t cifs //server_ip/share_name -o user=samba_user

It will ask for your password.

If you wish to use a host name rather then an ip address, add the host to the client /etc/hosts

A samba domain is again different from DNS and is used primarily for windows.

An alternate to samba is NFS (works if you have linux only). NFS4 is more secure then version 2 or 3. You can secure it further with kerberos, although that (kerberos) is a bit of a project.

NFS is a bit easier to manage as it uses Linux permissions.

Again, set initial permissions of the share on the Server.

The samba user foo can not mount a directory then can not read on the server and they can not write to a directory without write access server side.

---

### Post by 1serveyou on 2010-06-09
Thank you Bodhi, I will be trying these tonight! :thumbup:

---

### Post by 1serveyou on 2010-06-10
Good news and bad news, one part I forgot to mention was that I was mostly connecting with Windows 7 and OSX10.x. I spent a couple hours last night working on this and got further but still not 100% there yet. One of the shares seemed to work when I had the user name of the windows login the same as the user login for ubuntu, which it never asked me for a password it just allowed me to enter. But on my other 3 computers(Mac OSX10.6, MAC10.5, Win7 Virtual), it said I didn't have permissions, which is the correct result. Now on the 2 macs, you can change your login and password(On the win7 virtual, it wouldn't even let me choose that option and directly went to "cannot access"), and when I used the same user name as an allowable user, it worked. Now the fun part, I made another share, and I believe I had the same criteria, only thing I can think that was different is the actual directory permissions in ubuntu for that folder, I could only get the macs to connect to it when using the "Login with a different name." 

I'm guessing it is a folder permission on the actual ubuntu server, but I'm not 100% sure. Also I couldn't write to either of the folders I created for test purposes. I really have to get a grasp on all these permissions with folders/files/users.

But thank you again Bodhi, I appreciate the help. I'm not sure if I will get much time this weekend to work on it, but hopefully I will.

---


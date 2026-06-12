---
title: "Ubuntu / Samba / Windows - access control for specific shares"
date: 2008-11-17
forum: Server Platforms
---

### Post by cr0wn3r on 2008-11-17
I have a Ubuntu 8.10 system on my small office network acting as a file server using samba. 

I have the auth set to SHARE with guest access allowed on all shares, so the samba shares are all working and accessible to the everyone who is on the network - several windows PC's and a couple of remote PC's via vpn. Whenever anyone accesses the shares, they are using the guest user smbguest without ever having to type in a username or password. 

What I am now trying to do is:
- have one further specific share who's access is limited by a username and password
- be able to access this share (and if possible the other shares as well) from a windows machine but with a samba user other than 'smbguest', so that directories and files I create with this samba user will not be owned by the linux user 'smbguest' but by 'boris' - another linux user.

So far I have:
[LIST]
[*]created a new share directory on the ubuntu machine
[*]added this as a share using SWAT
[*]set this share to have a valid user list of 'manager' and turned guest access off
[*]opened /etc/samba/smbusers and added 'manager = boris' (I have a linux user already set up called boris and my understanding is that this links the samba user 'manager' to the existing linux user 'boris'...?)
[*]#smbpasswd -a manager  <--- to then enter the new password twice for the samba user 'manager'
[*]restarted samba
[/LIST]

Now all the other shares work as before, but when I try to access the new share from my windows vista machine it asks me for a username and password. Great. So I'm expecting to log in with 'manager' and the new password that I set for the samba user, but no matter what I try, how many times I reset the password, or double check what I wrote in the smbusers file, it wont give me access.

Sorry that's a bit of a long one, but I hope it makes sense. Ive been trying to figure this for ages... though I'm fairly sure that the problem Im having is the result of a large hole in my knowledge of this stuff.

Thanks

---

### Post by bab1 on 2008-11-17
This is a VIsta related issue.  You need to configure Samba to accept NTLMv2  login encryption.  See [**here**]("http://ubuntuforums.org/showthread.php?t=954691")

---

### Post by cr0wn3r on 2008-11-18
Thats great, thanks. It was indeed the problem. I ended up changing Vista to not use it with a reg tweak, rather than Samba to accept it.

I also found out that I had to have encrypt passwords on to connect via username / pw from a windows machine.

It's all working perfectly now.

Thanks again.

---


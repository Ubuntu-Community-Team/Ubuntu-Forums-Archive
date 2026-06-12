---
title: "samba configuration"
date: 2008-06-04
forum: Server Platforms
---

### Post by Necromantis on 2008-06-04
Hello all,

Sorry for the long post but I figure the more info I post the easier it would be to get some help.

I am trying to share some folders with SAMBA and of course it's not happening the way I would have hoped. 

I have 3 USB drives
mount on /usb1 /usb2 /usb3 (I keep it simple)

/usb1/Movies with /usb2/Movies with /usb3/Movies are merged together with unionfs under /mergeusb (works great)

usb3 has 3 users folders:
/usb3/user1
/usb3/user2
/usb3/user3


Ok that been the setup I want user1 to have rw on /usb1 /usb2 /usb3 and /usb3/user1 then read on /mergeusb (it would have rw by default through the /usb1-3 access anyway)

user2 should have read on /mergeusb and rw on /usb3/user2
user3 should have read on /mergeusb and rw on /usb3/user3

ok.. to do this I create 3 accounts: user1 user2 user3 under linux with the "sudo adduser" 

Then I used "sudo smbpasswd -a user1" to create the user + password and then "sudo smbpasswd -e user1" to activate the account. 

I did that for the 2 other accounts too.

/etc/samba/smb.conf
in there I put:

[global]
workgroup=msnhome
netbios name=Saturn
encrypted password=yes
security=user
guest account=nobody
invalid users=root

[Movies]
path=/mergeusb
browseable=yes
read list=user1 , user2 , user3

[usb1]
path=/usb1
browseable=yes
write list=user1

[usb2]
path=/usb2
browseable=yes
write list=user1

[usb3]
path=/usb3
browseable=yes
write list=user1

--- 

ok I didn't create the /usb3/user* shares yet because the above isn't working as it should.

Basically the user has to enter a username and password to gain access. However user2 and 3 can browse the /usb1 /usb2 /usb3 which of course I didn't want them to have access to. the section doesn't have there names in it I don't see how or where they got the access to list the folders??

So what did I miss? :confused:

---

### Post by freebeer on 2008-06-04
Did you try "browesable=no"?

I believe the "browseable=yes" command permits anyone to list what's on there, but the underlying file permissions would kick in to actually get read/write ability.  So user3 can see what's on user1's directory, but without read/write permissions they can't do anything with them.

---

### Post by Necromantis on 2008-06-05
browseable=yes makes the folder visible on the network
browseable=no makes the folder invisible on the network BUT it doesn't stop the user2 or user3 from entering the \\Saturn\USB1 and accessing the share folder that way... 

the USB1 folder ownership is set to root as well so I really can't see how or why user2 and user3 have read access to that folder :confused:

I have changed the [usb1 - 3]
browseable=no
read list=user1
write list=user1
public=no

restarted samba

and still user2 and user3 can access the folders usb1 usb2 and usb3 through \\Saturn\usb1-3

Err ??? help

---

### Post by kamaji792 on 2008-06-05
I wonder if the following option is what you need:

valid user = user1

That should only let user1  access the share.

All the best

---

### Post by Necromantis on 2008-06-09
Thanks that worked a treat !!

I found this web page after searching for valid users:

[http://oreilly.com/catalog/samba/chapter/book/ch06_02.html](http://oreilly.com/catalog/samba/chapter/book/ch06_02.html)

---


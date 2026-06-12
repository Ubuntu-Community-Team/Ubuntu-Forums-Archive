---
title: "Truecrypt &amp; Samba"
date: 2008-01-25
forum: Server Platforms
---

### Post by BlackGerm on 2008-01-25
Hi,

I just had the idea that I would like to use data encryption on my server as I have kind of sensible data on it.

Having a TrueCrypt running automatically on server boot and opening the container files is not an option for me.

I was thinking of the solution:
[LIST=1]
[*]Have several TrueCrypt containers that contain data. One for each wanted Samba share/user.
[*]When I log on on the Samba domain the username + password gets passed on to TrueCrypt and opens the container files for this user/share.
[/LIST]

If this is some how possible then I would like to get it working in a multi user environment.
Just now I would not know how I could tell samba to start TrueCrypt and hand over the username + password every time a user is logging in.

I know that I could put the container files inside a Samba share and use TrueCrypt on the client, but I guess that would be a huge performance issue opening the container file via a network connection. Also I would have quite some drive letters to deal with. One for the share containing the container file and an additional one to mount the container file to the client with TrueCrypt itself.

Is there any good solution to this? Any other suggestions on how to handle this?

Thanks
... Black

---

### Post by tlcoffee on 2008-01-25
that would be done via login scripts and not through samba. 

I take it that this is a windows environment that the users are logging into and mounting a linux file share via samba. you'll need to create login scripts for each user that uses samba, mount the drive (to be able to access the remote truecrypt container) and then the users workstation executes truecrypt with username + password.

something like that?

---

### Post by BlackGerm on 2008-01-25
Thanks for your quick reply.

I don't think the idea with login scripts is working, cause they are executed on the client that is login in.
But I would like to execute a script on the server to open up the TrueCrypt container, so that Samba can access it and provide the given data via a share to the client.

The way you suggest I am not sure about the performance and also it would create quite some drive mappings on the client side. One for accessing the samba share with the truecrypt container and a second one for accessing the data within the container file itself. 

Any hint is very welcome
... Black

---

### Post by tlcoffee on 2008-01-25
well, I understand but the deal is that you can not access a truecrypt container through any workstation or server without administrative access (because of specific drivers needed). the only administrative access the users will have is on their workstation...can someone verify?

---

### Post by BlackGerm on 2008-01-26
I checked the TrueCrypt website and you only need administrative rights for Windows.
Even so a script initiated by Samba could start TrueCrypt with root permissions, tell it which container file to mount and provide the password received by the client?

At least that is what I am hoping for.

Would anybody know how to achieve this?

Thanks
... Black

---


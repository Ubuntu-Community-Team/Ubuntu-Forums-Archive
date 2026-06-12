---
title: "Samba questions"
date: 2009-06-10
forum: Server Platforms
---

### Post by dimis80 on 2009-06-10
I have a couple of questions left in order to finalize my Ubuntu Server 8.04 LTS setup.

I have made the users in my corporate system and them i add some of them  with 

```
sudo smbpasswd -a dimitris
```

to my samba network giving the password without any problem.

the thing is that when i am trying to connect to folder "docs" for example through winXp i get the login screen but no luck on login in.

Why is that?

I add to /etc/samba/smbusers my clients like:

<ubuntuusername> = "<samba username>"
example: dimitris = "dimitris"

is that right?

Now why I cant login? All the folder that I have free I can see without problem.

Also I named my network name as "NEST"

I have changed in smb.conf the: workgroup = NEST but when I open windows network it gives me the path through Windows network -> Workgroup

What do you think?

---

### Post by superprash2003 on 2009-06-10
did you restart samba after making all these changes?

---

### Post by VeskoJl on 2009-06-10
:)

---

### Post by Iowan on 2009-06-10
> **dimis80 said:**
> 

<ubuntuusername> = "<samba username>"
example: dimitris = "dimitris"

is that right?
From [http://samba.org/samba/docs/man/Samba-Guide/secure.html#id2560202]("http://samba.org/samba/docs/man/Samba-Guide/secure.html#id2560202")
>  Create the username map file to permit the root account to be called Administrator from the Windows network environment. To do this, create the file /etc/samba/smbusers with the following contents:

####
# User mapping file
####
# File Format
# -----------
# Unix_ID = Windows_ID
#
# Examples:
# root = Administrator
# janes = "Jane Smith"
# jimbo = Jim Bones
#
# Note: If the name contains a space it must be double quoted.
#       In the example above the name 'jimbo' will be mapped to Windows
#       user names 'Jim' and 'Bones' because the space was not quoted.
#######################################################################
root = Administrator
####
# End of File
####


---

### Post by swerdna on 2009-06-11
Couple of things:
AFAIK all you need to add or change the credentilas for users on the Linux box is:
sudo smbpasswd -a name_of_user

name_of_user must pre-exist as a legit Linux user on the Linux box.

Then supply those creds from the windows box.

If you can't get in it's then probably due to either (a) the permissions contained in the configuration for the file share or (b) the Linux permissions on the directory that is shared. The two sets of permissions will convolve and produce a result that's the more restrictive of the two sets of options.

My money's on the permissions.

---

### Post by dimis80 on 2009-06-11
> **superprash2003 said:**
> did you restart samba after making all these changes?

Yes always.

---

### Post by dimis80 on 2009-06-11
> **swerdna said:**
> Couple of things:
AFAIK all you need to add or change the credentilas for users on the Linux box is:
sudo smbpasswd -a name_of_user

name_of_user must pre-exist as a legit Linux user on the Linux box.

Then supply those creds from the windows box.

If you can't get in it's then probably due to either (a) the permissions contained in the configuration for the file share or (b) the Linux permissions on the directory that is shared. The two sets of permissions will convolve and produce a result that's the more restrictive of the two sets of options.

My money's on the permissions.


I already done it with the way you describe.

The user first added in the ubuntu corporate system and then to samba...
the folders are full of access and I tried with a certain username in order to be opened...

---


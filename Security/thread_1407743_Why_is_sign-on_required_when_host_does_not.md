---
title: "Why is sign-on required when host does not"
date: 2010-02-15
forum: Security
---

### Post by unr-convert on 2010-02-15
I am using UNR 9.10.
I am attempting to use a printer on a Windows 7 system. I am connected through my home network. Same workgroup. The same printer is used by another Windows system (XP). No password is required, yet when I try to install the printer in UNR it insists that I sign in. Sign-in with what? There are no additional ids created on either system besides the default login.
Why does UNR want me to sjgn in and how do I get around this?
Thank you for your help.

---

### Post by movieman on 2010-02-15
Isn't that just Windows' crappy networking 'security'? If I remember correctly, I had to set my Linux password the same as my Windows password in order to access files on the Windows PC, otherwise it asks for a user name and password to access that machine.

And I doubt it's UNR asking for the information just to annoy you, it's almost certainly the Windows system with the printer demanding it.

---

### Post by unr-convert on 2010-02-15
But there is no password on the the windows machine and another windows machine can access the printer without signing in.

---

### Post by cariboo on 2010-02-15
Go to System->Administration->Printing, right click on the printer and select properties, next select Access Control and check the settings.

---

### Post by unr-convert on 2010-02-16
Thanks for the suggestion cariboo907. 
I cannot do this as Ubuntu will not even see the printer until I sign in.

---

### Post by cariboo on 2010-02-16
You could try reinstalling the printer, and set any access controls. If you do need to set access control initially, use a user name and password that is valid on the Windows 7 system. You may need to create a pssword on the Windows system.

---

### Post by unr-convert on 2010-02-16
Thanks for the prompt reply and the desire to help me.
Do you mean to reinstall the printer in Windows? I had a hard enough time making it work in Windows 7 and have no desire to monkey with it now. Remember it is already sharable and is shared by another Windows computer which is XP (i.e. not Windows 7). 
Samba insists that I sign in before I can install it. I was hoping to fix samba somehow to prevent this.
I would rather not have a password in Windows nor in UNR. The ability to print in UNR is not that important to me (as the computer is a netbook and it is seldom used at home any way).

---

### Post by cariboo on 2010-02-17
Just out of curiosity, what are the results when you enter the following command in a terminal:

```
smbclient -L <server name> -H%
```

where <server name> is the computer the printer is connected to. Do you get prompted to enter your password, or does it just print out something that looks like this:

```
smbclient -L risky -H%
Enter my password: 
Domain=[RISKY] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       Remote IPC
	print$          Disk      Printer Drivers
	SharedDocs      Disk      
	EPSONSty        Printer   EPSON Stylus Photo R340 Series
	ADMIN$          Disk      Remote Admin
	C$              Disk      Default share
Domain=[RISKY] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
```

The above is for the XP system, my Epson printer is connected to.

---

### Post by unr-convert on 2010-02-17
I have entered the suggested command. 
The following output is once with entering the root password (the olnly password there is) and the second time just hitting enter at the prompt:

user@acer-mini:~$ smbclient -L USER-DELL -H%
Enter user's password: 
session setup failed: SUCCESS - 0
user@acer-mini:~$ smbclient -L USER-DELL -H%
Enter user's password: 
Anonymous login successful
Domain=[OEMWORKGROUP] OS=[Windows 7 Home Premium 7600] Server=[Windows 7 Home Premium 6.1]

    Sharename       Type      Comment
    ---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
Anonymous login successful
Domain=[OEMWORKGROUP] OS=[Windows 7 Home Premium 7600] Server=[Windows 7 Home Premium 6.1]

    Server               Comment
    ---------            -------
    MIMI                 Ann's Desktop Dell
    USER-DELL            Bob's Desktop

    Workgroup            Master
    ---------            -------
    OEMWORKGROUP         USER-DELL
user@acer-mini:~$

---

### Post by cariboo on 2010-02-17
Is your netbook in the OEMWORKGROUP, or are you still in the default WORKGROUP?

---

### Post by unr-convert on 2010-02-17
Yes, all 3 computesr are in the oemworkbook.

---

### Post by cariboo on 2010-02-17
> **unr-convert said:**
> Yes, all 3 computesr are in the oemworkbook.

Is that a typo?

---

### Post by unr-convert on 2010-02-18
What typo? You mean computesr? Yes, I did reverse two letters. You mean 3 computers? Yes, I have a Win 7, and XP and the UNR netbook in my LAN.

---

### Post by cariboo on 2010-02-18
No I meant the workgroup name, in an earlier post it said OEMWORKGROUP, and in the post I was referring to you have oemworkbook. the systems all have to be in the same workgroup.

---


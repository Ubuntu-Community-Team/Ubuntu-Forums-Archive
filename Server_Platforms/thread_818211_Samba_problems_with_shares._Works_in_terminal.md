---
title: "Samba problems with shares. Works in terminal"
date: 2008-06-04
forum: Server Platforms
---

### Post by JanErikHiim on 2008-06-04
Try the best I can explain it in english.

I have a samba server at home with 4 computers.

When I restart samba I can not see the shares in either nautilus or Konquer.
But when I use the command:  smbclient -L 10.0.0.3

I get the result:

janerik@laptop:~$ smbclient -L 10.0.0.3
Password: 
Domain=[THERESE-LAPTOP] OS=[Unix] Server=[Samba 3.0.28a]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	dele_mappa      Disk      
	IPC$            IPC       IPC Service (therese-laptop server (Samba, Ubuntu))
	PDF             Printer   PDF
Domain=[THERESE-LAPTOP] OS=[Unix] Server=[Samba 3.0.28a]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
	HIIM                 SERVER
	JAN ERIK             LAPTOP
	THERESE              THERESE-LAPTOP
janerik@laptop:~$ 

So the shares are there.

But after maybe 10-20 minutes I can see the shares in "places"-networking and so on.

Why do I have that much delay??

Ive tryed setting up samba on 3 computers in the home network, and the sam results.
Can see the shares in terminal, but not in browsers??

---

### Post by kamaji792 on 2008-06-05
This is a bit of a guess.

Are all the computers set up with the same Workgroup name.  From your post I guess not.

In the /etc/samba/smb.conf file, set the **workgroup =** line to the same name for all the computers (I assume you are using Linux on all the computers - if not you will have to do the Windowsie thing to set the same workgroup).

All the best

---


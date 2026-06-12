---
title: "Adding a seperate samba share to a samba PDC"
date: 2006-02-17
forum: Server Platforms
---

### Post by 1oki on 2006-02-17
Hi all,
       Not quite sure if this is the right place to post this but here goes... 
I created a PDC with a guide I dug up here: 

[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

Everything works fine with that! I can logon and log off, and I have a samba share set up on the local PDC. The thing is, I want to add another Samba box to the share, and map it at logon. So when I logon to the domain it will show up as a drive. 

Im not a pro at Linux but im learning rather fast! I was thinking that I needed to mount the samba share on the PDC and then some how map it at logon... Can someone please help me! Also, I looked at the official Samba site, and if there is anything less confusing than that it’s much appreciated! Thanks

I was also wondering about LDAP, but thats a whole nother can of worms on its own... I need to get this working first!
-L
\\:D/

---

### Post by el3ktro on 2006-02-17
I'm not entirely sure what you mean. So ou have ONE Samba machine which has ONE shared directory, and you want to add a second shared directory?

Tom

---

### Post by 1oki on 2006-02-17
yes, I am using Samba as a domain controller which when logged on maps a directory as a shared drive. I also have a seperate samba box (buffalo terrastation) which I would like to map durring network logons. Both have samba... I want the TerraStation to connect to the Domain Controller and map that as a drive when logging on to that domain. Does that help any?

---

### Post by el3ktro on 2006-02-17
So you want to mount the Samba share on the PDC on the terrastation?

Tom

---

### Post by 1oki on 2006-02-17
No, I would like to mount the samba share on the Terrastation to the PDC... So when users log on they can have that terrastation as a drive...

---

### Post by 1oki on 2006-02-17
Oooo! I think I figured it out... I need to do a smbmount and then change the smb.config 
[allusers]
  path = /home/shares/allusers
  
to 

  path = (wherever I mounted it)

Yeah I think that should work... Thanks el3ktro for thinking about it for me... I wont be able to test it untill monday so If i have any problems I will surly be back! thanks!

---

### Post by el3ktro on 2006-02-17
Exactly,
on the PDC do "smbmount //terrastation/share" or you can also use mount -t smbfs (or cifs, it actually works better), and then in your smb.conf on the PDC add a new share with the mount point.

Tom

---

### Post by 1oki on 2006-02-17
:D 
Thanks for the confermation!

---


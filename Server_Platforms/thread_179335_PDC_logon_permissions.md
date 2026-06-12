---
title: "PDC logon permissions"
date: 2006-05-19
forum: Server Platforms
---

### Post by 1oki on 2006-05-19
Hello all! I recently and reluctantly switched from Ubuntu to Debian (Sarge) due to anti-virus support (centralized av server for my MS clients). As Im sure most of you know Ubuntu is a Debian based OS, so I figured I would post this question here because of how great all of you are! :D 

I am running a Debian PDC, and would like to setup a batch / logon file to call CACLS to set the permissions of the three groups (Domain Admins, Domain Users, and Guests) for the local drive and mapped drives. Domain admins would have full control, Users would be read write execute, guests would be read and execute. I know I can set the permissions by simply setting the permissions on the PDC, but I would like to do this through a batch. I am not the best batch writer, nor can I find any helpful tools or command lists on line. 

I do not have to do it this way of course, if any of you have set the user group rights for your PDC logon's please feel free to share! :) 

Thanks in advance

-L

---


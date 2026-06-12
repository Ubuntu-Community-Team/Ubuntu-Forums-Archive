---
title: "Samba PDC Information"
date: 2011-05-10
forum: Server Platforms
---

### Post by collisionystm on 2011-05-10
I just wanted to share some important information that I learned today about Samba domain controllers and Networking. Maybe it will help someone else out there....

I have 6 Sites all linked together with OPENVPN running on debian lenny/ubuntu boxes.
My samba PDC is here at the main site.

When I started this job, I had a major catastrophe, and long story short, I had to rebuild the PDC. Not entirely, but I did reinstall samba, bind9 and a few other things. 

I learned this very important fact...

If you have a Windows Machine that says, CANNOT FIND DOMAIN when attempting to Join, you need to check the following....

1.) Make sure that WINS is enabled in your smb.conf
2.) If your domain name is for example, Trash
Inside of your bind9 config files, you need to make sure you have an NS record for Trash that points to the box its on. I.E. 

```
$TTL 3D
@       IN      SOA     trash.Trash.       hostmaster (
                        2011051014      ;serial number
                        8H              ;refresh
                        2H              ;retry
                        4W              ;expiration
                        1D )            ;
;
@               NS      trash

```So make sure your WINS on your windows box is pointing to the PDC and make sure you have that record in your PDC bind

I guess I learned an important lesson about WINS and domains =/

What weird, is to join a  Windows Domain, All i needed to do was put in the DNS address into the box. No WINS required. It's WINS was pointing to the Samba and DNS to the windows.... 2 Worlds, same planet

---


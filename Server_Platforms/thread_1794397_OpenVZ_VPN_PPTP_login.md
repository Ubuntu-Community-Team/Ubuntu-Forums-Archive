---
title: "OpenVZ VPN PPTP login"
date: 2011-06-30
forum: Server Platforms
---

### Post by ghooton on 2011-06-30
Hope the gurus can help.
I have installed PPTP on a VPS running Ubuntu 9. The install (following the guides) went very well and everything installed and ran well
 
But when I try to log-in from a remote XP system the PPTP gets to the login screen and then stalls until it finishes with an (XP) error 806 or 619. The same machine works well to other PPTP servers so I do not think I have router or other issues. The company supplying the VPS assures me that PPTP is enabled. 
 
I can see the connection in the PPTP user list on the server as "PPP Interface Unknown 124.157.77.108 06:10 45.22.67.00 172.198.2.50 username unknown" so connection and encryption must be working correctly.
 
The IP addresses all are correct (sorry for security they are not the real addresses) and appear to be valid ( 124....... is the NZ end, 45..... is the server ip, 172.198... is I think a valid internal address). Perhaps the clue is in the "PPP Interface unknown and/or username unknown". The /etc/ppp/chap-secrets seems OK
"
# Secrets for authentication using CHAP
# client server secret IP addresses
"" vps "" "*"
 
(this entry should be an "allow all" for testing )
 
Can anyone advise next diagnosis steps please 
 
Thanks and regards

---


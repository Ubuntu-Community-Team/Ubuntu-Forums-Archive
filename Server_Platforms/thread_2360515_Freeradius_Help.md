---
title: "Freeradius Help"
date: 2017-05-05
forum: Server Platforms
---

### Post by brierley on 2017-05-05
Hello,

1st post on here so sorry if its in the wrong spot.
I have a freeradius setup however I am struggling to add the additional functionality I need.

Its setup using MYSQL as the database backend and works fine however I would like to achieve the following setup:

Access request comes in to freeradius server (FreeRADIUS_A)
The freeradius server (FreeRADIUS_A) forwards the authentication to a remote server (Also a radius server)(FreeRADIUS_B)
ONLY the username and password is checked on the remote server (FreeRADIUS_B)
If the user passes authentication on the remote server the remote server(FreeRADIUS_B) responds to the original server (FreeRADIUS_A) with an Access accept ONLY.
The original server (FreeRADIUS_A) now responds to the original client / NAS with a list of RADIUS ATTRIBUTES which I will configure.

I have searched high and low for a way to do so and other than the generic concept I am no further into actually implementing this.
I understand the term may be Radius Proxy where (FreeRADIUS_A) is therefore a NAS however I want (FreeRADIUS_A) to be responsible for providing RAD-REPLIED & RAD-GROUP-REPLIES etc.

Any help on this would be ace !!

Main reason for doing so is I want to use (FreeRADIUS_B) as a 2FA server, and implementing all of this on one Box is a bit of a strain and also isn't too straight forward to generate RADREPLYS.
Also if I can get a working solution for this I can replicate this elswhere and just point authentication requests to (FreeRADIUS_B)

Hope this makes sense

---


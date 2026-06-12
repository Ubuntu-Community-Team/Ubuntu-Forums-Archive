---
title: "Freeradius - Lock down one user to accessing from 1 IP address."
date: 2016-11-01
forum: Security
---

### Post by mcparty2 on 2016-11-01
Hi folks,

I am using Freeradius successfully as a basic level of authentication for some cisco equipment and several Ubuntu servers (using the radius PAM module). Freeradius is looking at the local system users on the Freeradius server for authentication (not using mysql).

Does any one know of a method locking down a user to one IP. So authenticating a user ONLY if he comes from a single IP with the correct IP address?
I have had a look at the Freeradius wiki however I am struggling to decipher any usable information.

I'd appreciate any assistance. 

Thank you for reading.

---

### Post by ian-weisser on 2016-11-02
Consider an IPTables rule. Packets from the wrong IP get ignored.

---

### Post by mcparty2 on 2016-11-03
Thanks for the reply though I don't think that would work as I have a number over users that can access devices from a VPN using 2FA.
I want to limit a system user with no 2FA to only get a sucessful auth reply if they try accessing from a particular IP. 
This is so the VPN users cannot use that system account.

I think I may have to go down the MySQL route as I am also wanting to lock out radius users after x amount of failed login attempts. However, if there are any other ideas I am open to suggestions.

Thank you

---

### Post by mcparty2 on 2016-11-10
You know it's bad when you are searching for answers and you find your own post in your searches. 
I have Freeradius now working with MySQL and 2FA. My users are able to authenticate though I have a single system user which I want to tie down to the one IP address. 

I shall persevere some more and report back any results it may be useful to others. Or if anyone has any suggestions... :) 

Thanks for reading I appreciate your time.

---

### Post by mcparty2 on 2016-11-11
I can see documentation on how to lock authorisation to a mac address though my calling-station-id is an IP address not a mac. I think the principle will be the same... This is what the packet sent from the client shows...

```

rad_recv: Access-Request packet from host 127.0.0.1 port 7917, id=77, length=145
    User-Name = "systemuser"
    User-Password = "**********"
    NAS-IP-Address = 10.10.10.1
    NAS-Identifier = "sshd"
    NAS-Port = 6892
    NAS-Port-Type = Virtual
    Service-Type = Authenticate-Only
    Calling-Station-Id = "10.10.10.5"

```

I am going to see if I can get something to work, if not i'll go to the Freeradius folks and see if they can help.
I'll close this thread. But thanks for reading and Ian-Weisser for his input.

---


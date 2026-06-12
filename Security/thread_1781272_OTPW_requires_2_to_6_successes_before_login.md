---
title: "OTPW requires 2 to 6 successes before login"
date: 2011-06-13
forum: Security
---

### Post by rfreytag on 2011-06-13
I have been experimenting with OTPW (1.3) by pulling down (apt-get install libpam-otpw).  I configured /etc/ssh/sshd_config and /etc/pam.d/sshd as given on the development page ([http://www.cl.cam.ac.uk/~mgk25/otpw.html]("http://www.cl.cam.ac.uk/%7Emgk25/otpw.html")).  

The problem is that when I attempt to log in and type the password correctly I get asked for 2 to 6 more OTPW password challenges before I am let in.  I know that I am typing my password correctly because if I mistype my password it will ask me for the same numbered password again.  If I get the password correct it asks for a DIFFERENT password - again 2 to 6 times.  

This is NOT associated with the 3 pwd request associated with multiple simultaneous logins to the OTPW-enabled account.  

I am using Ubuntu Server 10.04 LTS with the latest upates.  

Thanks a lot for any thoughts - I've been spinning on this for a while and am out of ideas of what might be the cause of this problem.

---


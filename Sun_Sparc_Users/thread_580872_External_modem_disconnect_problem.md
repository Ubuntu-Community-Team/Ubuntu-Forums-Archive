---
title: "External modem disconnect problem"
date: 2007-10-19
forum: Sun Sparc Users
---

### Post by petrus1928 on 2007-10-19
Hello & greetings from Queensland.
I'm seeking help for a friend's problem where the external modem connects briefly then disconnects after 1 or 2 seconds.He's a newbie & using dapper, I have some more experience, but not a lot.
The modem is an external 56k model. It 's 'not found' when trying to set up in 'Network settings'. However kppp finds it and dials out then hangs up after a very brief connection.
Relevant log info is: exit code=16, the link was terminated by the modem hanging up.  terminating connection due to lack of activity. 
Excerpt from /var/log/messages: ct 19 10:44:45 localhost pppd[5361]: pppd 2.4.4b1 started by bert, uid 1000
Oct 19 10:44:45 localhost pppd[5361]: Using interface ppp0
Oct 19 10:44:45 localhost pppd[5361]: Connect: ppp0 <--> /dev/ttyS0
Oct 19 10:44:45 localhost pppd[5361]: Warning - secret file /etc/ppp/pap-secrets has world and/or group access
Oct 19 10:44:46 localhost pppd[5361]: local  IP address 203.220.187.113
Oct 19 10:44:46 localhost pppd[5361]: remote IP address 203.220.247.113
Oct 19 10:44:46 localhost pppd[5361]: primary   DNS address 203.194.56.150
Oct 19 10:44:46 localhost pppd[5361]: secondary DNS address 203.194.27.57
Oct 19 10:45:35 localhost pppd[5361]: Terminating connection due to lack of activity.
Oct 19 10:45:35 localhost pppd[5361]: Connect time 0.9 minutes.
Oct 19 10:45:35 localhost pppd[5361]: Sent 20774 bytes, received 174213 bytes.
Oct 19 10:45:41 localhost pppd[5361]: Connection terminated.
Oct 19 10:45:41 localhost pppd[5361]: Modem hangup
Oct 19 10:45:41 localhost pppd[5361]: Exit.

Additionally, altho' the modem is 64K, the  ISP reports a 28.8 k connection.

I've checked DialupModemHowto/SetUpDialer from my computer and noted the relevant instructions, but won't be able to get back to him for a few days.  Would the steps outlined in DialupModemHowto/SetUpDialer resolve this problem, or should I look elsewhere?  
Thanks a bundle for suggestions

---


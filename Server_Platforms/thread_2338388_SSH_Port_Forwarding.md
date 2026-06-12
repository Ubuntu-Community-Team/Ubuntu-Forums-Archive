---
title: "SSH Port Forwarding"
date: 2016-09-27
forum: Server Platforms
---

### Post by freakky on 2016-09-27
I'm having trouble connecting the Crashplan app installed on the ssh client to the Crashplan daemon on the headless server.

Details:
[LIST]
[*]Building my first file server after running Ubuntu since 2009; we're beginning to accumulate computers at the house and a file server would be nice
[*]I'm following the instructions here: [https://support.code42.com/CrashPlan/4/Configuring/Using_CrashPlan_On_A_Headless_Computer](https://support.code42.com/CrashPlan/4/Configuring/Using_CrashPlan_On_A_Headless_Computer) (Crashplan 4.7.0 on both client and server)
[*]I adjusted the existing Crashplan authentication token on the client with the authentication token from the remote computer, and changed port to 4200 on the client
[*]I was able to tunnel to the server via Putty
[*]After launching the Crashplan app (located on the client, forwarded to the server) the server file /var/log/auth.log shows:
[/LIST]

Sep 27 18:11:30server sshd[1494]: error: connect_to server port 4243: failed.
Sep 27 18:12:31server sshd[1494]: message repeated 15 times: [ error: connect_toserver	 port 4243: failed.]

I'm assuming it's a setting in the ssh configuration file on the server, but haven't successfully troubleshooted from here.  Any thoughts on how to troubleshoot?
Any help would be appreciated.

---

### Post by Vegan on 2016-09-28
i assume the ports are open on the firewall

---

### Post by freakky on 2016-09-29
When I check <ufw status> I get "Status: inactive"
I assume the firewall is not the problem.

---

### Post by ian-weisser on 2016-09-30
ufw is merely a frontend for iptables, which is always active.
ufw status inactive simply means ufw is inactive. It doesn't say anything about iptables.
To check iptables, try 'sudo iptables -L'

If you find crashplan to be annoying or complicated, native Ubuntu server applications (that we support) are also available.

---

### Post by eetorres on 2016-09-30
This page may have useful information:

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

### Post by freakky on 2017-02-22
Typing 'sudo iptables -L' shows Input, Forward and Output are set to ACCEPT.

Using netstat, I see the port is listening, but it's 127.0.0.1:4243 instead of 0.0.0.0:4243.  I assume this wouldn't allow a connection from the client (via local port forwarding) to the server on that port.  I can telnet to any port that shows listening 0.0.0.0:XXXX, but not to a port listening 127.0.0.1:XXXX.

I thought about redirecting the ports internally after connecting via a 0.0.0.0 port.  But that doesn't work, stating address (4243) is already in use.

Any help would be greatly appreciated.  I have been toying with this problem for much too long.

---

### Post by darkod on 2017-02-23
Correct, any port listening only on 127.0.0.1 is not accessible from other machines. Only from that local machine itself.

Have you checked that Crashplan app to see if you can tell it to listen on 0.0.0.0 (or the correct LAN IP of the server)? That is probably the correct way to do it, there surely is a way to modify the config to listen on the IP/interface you want.

---


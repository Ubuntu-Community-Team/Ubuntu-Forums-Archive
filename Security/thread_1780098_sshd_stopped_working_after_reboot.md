---
title: "sshd stopped working after reboot"
date: 2011-06-11
forum: Security
---

### Post by bilkay on 2011-06-11
I've been using ssh for a LONG time to connect my laptop to my desktop with no problems. I use a non-standard port (nnnnn) and keys. After a power outage that caused a shutdown and reboot, I can no longer ssh into the desktop. The only changes I've made are updates (laptop and desktop both running ubuntu 10.04).

$ ssh -p nnnnn Desktop
ssh: connect to host Desktop port nnnnn: Connection refused

No messages are generated in any of the logs on Desktop!

$ /usr/sbin/sshd -T
port nnnnn
protocol 2
addressfamily any
listenaddress 0.0.0.0:12023
listenaddress [::]:12023
usepam 1
serverkeybits 768
logingracetime 120
keyregenerationinterval 3600
x11displayoffset 10
maxauthtries 6
maxsessions 10
clientaliveinterval 0
clientalivecountmax 3
permitrootlogin no
ignorerhosts yes
ignoreuserknownhosts no
rhostsrsaauthentication no
hostbasedauthentication no
hostbasedusesnamefrompacketonly no
rsaauthentication yes
pubkeyauthentication yes
kerberosauthentication no
kerberosorlocalpasswd yes
kerberosticketcleanup yes
gssapiauthentication no
gssapikeyexchange no
gssapicleanupcredentials yes
gssapistrictacceptorcheck yes
gssapistorecredentialsonrekey no
passwordauthentication no
kbdinteractiveauthentication no
challengeresponseauthentication no
printmotd no
printlastlog yes
x11forwarding yes
x11uselocalhost yes
strictmodes yes
tcpkeepalive yes
permitblacklistedkeys no
permitemptypasswords no
permituserenvironment no
uselogin no
compression delayed
gatewayports no
usedns yes
allowtcpforwarding yes
useprivilegeseparation yes
pidfile /var/run/sshd.pid
xauthlocation /usr/bin/xauth
authorizedkeysfile .ssh/authorized_keys
authorizedkeysfile2 .ssh/authorized_keys2
loglevel INFO
syslogfacility AUTH
hostkey /etc/ssh/ssh_host_rsa_key
hostkey /etc/ssh/ssh_host_dsa_key
acceptenv LANG
acceptenv LC_*
subsystem sftp /usr/lib/openssh/sftp-server
maxstartups 10:100:10
permittunnel no
permitopen any

---

### Post by CVGH on 2011-06-11
Try setting loglevel VERBOSE then run:
sudo /etc/init.d/ssh restart
See if you can get in after that.
If not, see what /var/log/auth.log says....

---

### Post by bilkay on 2011-06-11
> **CVGH said:**
> Try setting loglevel VERBOSE then run:
sudo /etc/init.d/ssh restart
See if you can get in after that.
If not, see what /var/log/auth.log says....

I got log entries when ssh restarted, but nothing when trying to remotely log in:

Jun 11 16:41:01 Desktop sshd[4107]: Received signal 15; terminating.
Jun 11 16:41:01 Desktop sshd[4143]: Server listening on 0.0.0.0 port nnnnn.
Jun 11 16:41:01 Desktop sshd[4143]: Server listening on :: port nnnnn.

---

### Post by CVGH on 2011-06-11
Did it actually say 0.0.0.0, or are you just keeping your IP private?
Did you update to 10.04 before the power loss?

---

### Post by bilkay on 2011-06-11
> **CVGH said:**
> Did it actually say 0.0.0.0, or are you just keeping your IP private?
Did you update to 10.04 before the power loss?
It actually said '0.0.0.0'! Any ideas where that came from?

(update) the sshd_config file contains a line "#ListenAddress 0.0.0.0" which I assume is commented out.

(I haven't updated to 10.04 - I've been running that since it came out. I just run regular updates when notified)

---

### Post by CVGH on 2011-06-11
Well, it looks like something is sending the SIGTERM signal to the ssh daemon. Maybe check /var/log/messages? Got any firewall configs running? The server listening 0.0.0.0 port 12023 is correct BTW....

---

### Post by bilkay on 2011-06-12
This is frustrating! I modified iptables on Desktop to produce the following, thinking it should at least give me some clue as to what's happening:

```
#iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
LOG        all  --  Laptop               anywhere            LOG level warning 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```But I'm still getting nothing in any of the log files in /var/log! I tried pinging Desktop - which succeeded - but nothing in the logs on that either.

(update) I tried all log levels 0 - 7 with no change in results. I also tried making the same changes to iptables on Laptop and got the result I expected, i.e., log entries in /var/log/syslog when I pinged Laptop from Desktop.

Btw, thanks for trying to help.

---

### Post by CVGH on 2011-06-12
I wonder if you went back to trying it without using keys for authentication?
I've installed multitail and run with this command to watch my logs:
```
multitail -R 2 -l "netstat -atpvn" -ci green /var/log/auth.log -ci blue  /var/log/messages
```Maybe that will help you see what is going on better....

---

### Post by bilkay on 2011-06-13
It's getting stranger! This morning, I could ssh to Desktop from Laptop! Also, iptables logging mysteriously started working as expected on Desktop. The only thing that still doesn't work is sshfs. In all this, I didn't do anything to the system.

Could this be some kind of hardware glitch?

---

### Post by CVGH on 2011-06-15
Is it still working ok?

---

### Post by bilkay on 2011-06-15
> **CVGH said:**
> Is it still working ok?
With the exception of sshfs. I'm at a loss to explain what happened.

---

### Post by qiet72 on 2012-07-11
Hi,

I just solved my ssh gssapi kerberos problem.  If you use "gssapistrictacceptorcheck yes" in /etc/ssh/sshd_config, then you need to make sure all the host principals sshd needs are in the /etc/krb5.keytab file and that the client has an fqdn in /etc/hosts file.  But if you use "gssapistrictacceptorcheck no", then the only thing you need is a valid /etc/krb5.keytab with some host principals in it.

qiet72

---


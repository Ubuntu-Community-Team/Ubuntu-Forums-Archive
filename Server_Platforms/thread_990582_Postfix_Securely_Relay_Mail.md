---
title: "Postfix: Securely Relay Mail"
date: 2008-11-22
forum: Server Platforms
---

### Post by Dr Small on 2008-11-22
[CENTER][SIZE="6"]Securely Relaying Mail[/SIZE]
[SIZE="5"]with Postfix[/SIZE][/CENTER]


**_Introduction_**
Postfix's default action for relaying mail is to allow the local system (localhost) and the local area network to relay mail through it's SMTP server. While this is relatively secure, it does not allow clients to send their mail through the server's SMTP server while off the network.

The simple (unsecure) way to fix this problem, would be to simply allow any network to relay mail through the SMTP server. This my friend, is a spammers dream SMTP server. Open relaying allows anyone to connect to your SMTP server and send an email from any location to any location.

Unfortunately, most Internet Service Providers and uninformed system admin's install Postfix and think the tinkering has ended, which inevitably allows spammers to use their server for bulk mailing of their fake products.

I will attempt to explain to you, in the simplest way possible, of setting up SMTP-AUTH, which will only allow authorized users to send mail through the SMTP server, denying all others. This will end the open relaying issue.

**_Getting Started_**
Assuming you already have Postfix installed, we will begin by installing SASL:
```
sudo apt-get install libsasl2-2 sasl2-bin
```

We need to edit SASL's configuration file so it can start properly, and set a few other options in it.
```
sudo vim /etc/default/saslauthd
```

You should see "START=no" at the top of the file. Change this to "START=yes". Add the following lines after your START variable:
```
PWDIR="/var/spool/postfix/var/run/saslauthd"
PARAMS="-m ${PWDIR}"
PIDFILE="${PWDIR}/saslauthd.pid"
```

Set the OPTIONS variable to read:
```
OPTIONS="-c -m /var/spool/postfix/var/run/saslauthd"
```

In the end, your edits should look as follows:
```
START=yes
PWDIR="/var/spool/postfix/var/run/saslauthd"
PARAMS="-m ${PWDIR}"
PIDFILE="${PWDIR}/saslauthd.pid"
OPTIONS="-c -m /var/spool/postfix/var/run/saslauthd"
```

Now we should reconfigure SASL to change it's root directory and place it in Postfix's chroot:
```
sudo dpkg-statoverride --force --update --add root sasl 755 /var/spool/postfix/var/run/saslauthd
```

Start SASL:
```
sudo /etc/init.d/saslauthd start
```


_**Editing Postfix**_
Now that you have SASL all setup, let's configure Postfix to use SASL.

(This step may not be required, as I went back and saw that I did not have to do it. Please check this step before continuing.)
```
cd /etc/postfix/sasl/
```

If this directory exists, contains a file called "smtpd.conf" and the file contents are:
```
pwcheck_method: saslauthd
mech_list: plain login
```

Then you are good to go. Otherwise, please follow these steps:
```
cd /etc/postfix/
sudo mkdir sasl
cd sasl/
sudo vim smtpd.conf
```
And put the contents in this file that you see in the previous codeblock.


Next, we need to add some settings to Postfix's main.cf file by the usage of the postconf command!
```
sudo -i
postconf -e 'smtpd_tls_auth_only = yes'
postconf -e 'smtp_use_tls = yes'
postconf -e 'smtpd_use_tls = yes'
postconf -e 'smtp_tls_note_starttls_offer = yes'
postconf -e 'smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key'
postconf -e 'smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt'
postconf -e 'smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem'
postconf -e 'smtpd_tls_loglevel = 1'
postconf -e 'smtpd_tls_received_header = yes'
postconf -e 'smtpd_tls_session_cache_timeout = 3600s'
postconf -e 'tls_random_source = dev:/dev/urandom'
mkdir /etc/postfix/ssl
cd /etc/postfix/ssl

```

Now we will begin generating our SSL keys and certificate. You will be prompted by openssl for details about your domain, state, email, organization name, etc. Here is a little hint as to what you should enter when prompted:
```
commonName              = mycroftserver.homelinux.org
stateOrProvinceName     = Colorado
countryName             = US
emailAddress            = myemail@mysubdomain.domain.com
organizationName        = Mycroft Server
organizationalUnitName  = The Private Server of Dr Small
```

Start generating those keys!
```
openssl genrsa -des3 -rand /etc/hosts -out smtpd.key 1024
chmod 600 smtpd.key
openssl req -new -key smtpd.key -out smtpd.csr
openssl x509 -req -days 3650 -in smtpd.csr -signkey smtpd.key -out smtpd.crt
openssl rsa -in smtpd.key -out smtpd.key.unencrypted
mv -f smtpd.key.unencrypted smtpd.key
openssl req -new -x509 -extensions v3_ca -keyout cakey.pem -out cacert.pem -days 3650
```

Now we can restart Postfix:
```
/etc/init.d/postfix restart
exit
```


**_Verifying_**
Let's check with telnet, to see if everything went as planned:
```
telnet localhost 25
```

The server should greet you, similar to this:
```
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 mycroftserver.homelinux.org ESMTP Postfix (Ubuntu)
```

Now type:
```
EHLO localhost**<return>**
```

The server should reply. Look for:
```
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
```

If it is listed there, then everything is working as planned. Now from an email client off the network (or connecting to your WAN IP), setup the SMTP server and use Authentication and encryption. Verify that emails send.

Now we will try it from a spammers level:
```
telnet *yourwanip* 25
```

Now we'll see if relaying is actually denied:
```
HELO server**<return>**
MAIL FROM: spammer@spamcity.net**<return>**
RCPT TO: user@server1.net**<return>**
```

The server should then return:
```
554 5.7.1 <user@server1.net>: Relay access denied
```

Congratulations, Postfix is now securely setup for relaying :)

PS: If I have made any mistakes anywhere, please correct me and I will fix it.




**_External Links_**
[Ubuntu Help: Postfix]("https://help.ubuntu.com/community/Postfix")
[Open Relay Testing]("http://spamlinks.net/prevent-secure-relay-test.htm")

---

### Post by MJN on 2008-11-24
Great post Dr Small. Just one comment:
 
If one of the fundamental goals of this guide is security then given you are using TLS you should insist that all connecting clients use TLS when authenticating with a plaintext mechanism otherwise their username/password will be sent in the clear and hence be vulnerable to sniffing.
 
You do this by setting **smtpd_tls_auth_only = yes** (you had it set to the default 'no').
 
Mathew

---

### Post by Dr Small on 2008-11-24
> **MJN said:**
> [...] then given you are using TLS you should insist that all connecting clients use TLS when authenticating with a plaintext mechanism otherwise their username/password will be sent in the clear and hence be vulnerable to sniffing. [...]

You are correct. Thanks for pointing this out to me. I will correct this issue.

Dr Small

---

### Post by batfastad on 2009-02-04
Hi
Just tried following this tutorial but got an error when trying this command:
```
sudo dpkg-statoverride --force --update --add root sasl 755 /var/spool/postfix/var/run/saslauthd
```

The error I get is:
--update given but /var/spool/postfix/var/run/saslauthd does not exist

I'm running Ubuntu 8.04 in a virtual private server from VPSlink.com, so it could be my environment is slightly different.

Any ideas?

Thanks, B

---

### Post by Dr Small on 2009-02-04
> **batfastad said:**
> Hi
Just tried following this tutorial but got an error when trying this command:
```
sudo dpkg-statoverride --force --update --add root sasl 755 /var/spool/postfix/var/run/saslauthd
```

The error I get is:
--update given but /var/spool/postfix/var/run/saslauthd does not exist

I'm running Ubuntu 8.04 in a virtual private server from VPSlink.com, so it could be my environment is slightly different.

Any ideas?

Thanks, B
I'm pretty sure I got the same thing on Debian too. Have you tried moving on to see if it would affect it any? Recently I setup SMTP Auth on Debian and a few things were different so I had to keep tinkering at it to get it right.

---

### Post by ericwait on 2009-06-07
When I do:
```
EHLO localhost
```
I only see 
```
250-AUTH PLAIN
250-AUTH=PLAIN
```
I copied the settings for smtpd.conf

What do you think is wrong?

---

### Post by madmacz on 2010-01-09
Everything except for the last part went right. I get the following error:

RCPT TO:lobomacz@gmail.com
550 5.1.1 <lobomacz@gmail.com>: Recipient address rejected: User unknown in local recipient table

What could be the problem?

---


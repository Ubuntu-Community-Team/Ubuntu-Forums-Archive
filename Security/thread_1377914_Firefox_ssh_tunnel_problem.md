---
title: "Firefox ssh tunnel problem"
date: 2010-01-10
forum: Security
---

### Post by hastur_2 on 2010-01-10
I have a netbook running 8.04 that I want to set to ssh tunnel through my server, which is also running 8.04.  The server was upgraded in place from 6.06.  I have the same version of ssh set up on both machines and the config files haven't been changed.  I can connect to the server using either the machine name or the IP address, but if I use the address (192.168.1.5) I have to put my user name in front.  Both machines have a user account with the same name.  I set up RSA keyed access per the usual method without complaint.

The server shows a valid connection from the laptop, whether I use the command line or gSTM, but when I try to tunnel, no data is passed.  

I tell Firefox to use the tunnel by setting the manual proxy configuration to 127.0.0.1 port 8118 and nothing comes through.  It works normally when the proxy is turned off.  The laptop was set to use port 8118.

Any thoughts?  I'm stumped.

Thanks

Rob

---

### Post by BkkBonanza on 2010-01-10
What command are using to setup the tunnel?

The easiest, best way is to use a SOCKS5 proxy which is the -D (dynamic) option for ssh. eg.

ssh user@server -D 8118 -N

In gSTM this is selected by adding dynamic type and the port#. You give it the path for your key file but it doesn't work with ~ you have to use /home/user

In Firefox you would choose SOCKS5 localhost:8118.

This should work very well. I use it daily, almost.

---

### Post by hastur_2 on 2010-01-10
I tried the following:

rob@rob:~$ ssh rob@satchel -D 8118 -N

Firefox settings: Manual proxy configuration, Proxy 127.0.0.1, Port 8118, Use this for all.
No joy

Change Firefox from 127.0.0.1 to localhost
No joy

Killed ssh with Ctrl-C

Change to rob@rob:~$ ssh rob@192.168.1.5 -D 8118 -N
Leave Firefox alone
No joy.

Change Firefox back to 127.0.0.1
No joy.

Satchel is resolved correctly using the hosts file and pings fine.

I also tried it w/o the localhost, 127.0.01 exception at the bottom of the Firefox config window.

See why I've been scratching my head?

Thanks,

Rob

PS Socks 5 was checked in Firefox in all cases.

---

### Post by HermanAB on 2010-01-11
Debug in stages.  First ensure that SSH server is reachable, then set up a socks connection and ensure that it works, only then try Firefox.

Eg:
Restart sshd on server:
$ sudo service sshd restart

Log in locally on server to ensure it works:
$ ssh localhost -l johndoe
password

Log in remotely to ensure routing works:
$ ssh server -l johndoe
password

Set up Socks proxy from from remote:
$ ssh johndoe@server -D 8118

If not, enable SSH error messages:
$ ssh -vvv johndoe@server -D 8118

Check the proxy is working again and watch the error messages:
$ telnet localhost 8118
should get a response from server


Once all problems are resolved try Firefox.

---

### Post by noway2 on 2010-01-11
In your firefox configuration, under manual proxy did you check that it is a SOCKS proxy?

---

### Post by hastur_2 on 2010-01-11
> **HermanAB said:**
> Debug in stages.  First ensure that SSH server is reachable, then set up a socks connection and ensure that it works, only then try Firefox.

Eg:
Restart sshd on server:
$ sudo service sshd restart

[COLOR=Purple]"service" not installed, ps -aux shows /usr/sbin/sshd running[/COLOR]


Log in locally on server to ensure it works:
$ ssh localhost -l johndoe
password

[COLOR=Purple]Works[/COLOR]

Log in remotely to ensure routing works:
$ ssh server -l johndoe
password

[COLOR=Purple]Works[/COLOR]

Set up Socks proxy from from remote:
$ ssh johndoe@server -D 8118

[COLOR=Purple]Works[/COLOR]

If not, enable SSH error messages:
$ ssh -vvv johndoe@server -D 8118

Check the proxy is working again and watch the error messages:
$ telnet localhost 8118
should get a response from server

[COLOR=Purple]Installed telnet,

rob@rob:~$ telnet localhost 8118
Trying 127.0.0.1...
Connected to rob.
Escape character is '^]'.

Hangs[/COLOR],[COLOR=Purple] no response, closed with CTRL-C
[/COLOR] 
Stop here and ask for comments/help.  :)

Once all problems are resolved try Firefox.



In your firefox configuration, under manual proxy did you check that it is a SOCKS proxy?      [COLOR=Purple]The SOCKS v5 radio button was chosen.  I hope that's what you meant.[/COLOR]

It looks like sshd on the server is refusing the connection.

Thanks for the help.

Rob

---

### Post by BkkBonanza on 2010-01-11
That response from telnet is correct. You need to talk SOCKS5 protocol after the connection or it will disconnect you. SOCKS5 is a binary protocol so it wouldn't be easy to mimic at the telnet prompt.

BTW, Your Firefox setting should look like this (with your port# of course), 
[IMG]http://dl.dropbox.com/u/3115138/FF.png[/IMG]

---

### Post by BkkBonanza on 2010-01-11
You can try to test the proxy at the command line using,

curl --socks5 localhost:8118  google.com

You should get something from google output on screen. Usually a redirect page but no matter any text from google means it's working.

---

### Post by hastur_2 on 2010-01-12
> **BkkBonaza said:**
> You can try to test the proxy at the command line using,

curl --socks5 localhost:8118  google.com

You should get something from google output on screen. Usually a redirect page but no matter any text from google means it's working.


rob@rob:~$ curl --socks5 localhost:8118 google.com
<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>301 Moved</TITLE></HEAD><BODY>
<H1>301 Moved</H1>
The document has moved
<A HREF="http://www.google.com/">here</A>.
</BODY></HTML>


Looks good to me.

Fixed Firefox config.  I had localhost:8118 set for http and the "Use this for all.." checked.  I changed it to SOCKS only and it works.  

It looks like I found the problem.  Woo hoo.  Thank you for the help.  Now on to running evolution through tsocks.

Rob

---

### Post by BkkBonanza on 2010-01-12
Are you sure you have to run Evolution using tsocks?
You can select menu System, Prefs, Network Proxy and set a SOCKS proxy there that is supposed to be used by all Gnome apps. I don't use Evolution but I would have thought it would use the system proxy settings. That's also another way to set Firefox - leave FF on "use system settings", and then change on menu as above.

---

### Post by hastur_2 on 2010-01-14
> **BkkBonaza said:**
> Are you sure you have to run Evolution using tsocks?
You can select menu System, Prefs, Network Proxy and set a SOCKS proxy there that is supposed to be used by all Gnome apps. I don't use Evolution but I would have thought it would use the system proxy settings. That's also another way to set Firefox - leave FF on "use system settings", and then change on menu as above.

After a bit of research, it looks like Evolution supports SSL SMTP and POP, so I think I'm done.  I was looking for a solution to possible snooping at public hotspots while using my netbook.  My traffic can be encrypted from my machine to my home server for web traffic or from the netbook to my e-mail server.  Woo Hoo.

Thanks for the help.

Rob  :D

---

### Post by BkkBonanza on 2010-01-15
It's likely not a concern for you regarding general snooping but in high security/paranoia situations you also need to consider that Firefox by default leaks DNS info when using a ssh tunnel. This is because DNS lookups are done locally despite page traffic being throught the tunnel. There is an about:config setting that tells FF to use DNS through the tunnel as well, which plugs that leak. 

About:config variable to set is,

network.proxy.socks.remote_dns either true or false

You may also find it handy to use FoxyProxy plugin to manage this and make proxy changes quickly.

---


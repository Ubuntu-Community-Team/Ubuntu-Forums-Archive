---
title: "FreeRADIUS on ubuntu 8.04.2"
date: 2009-03-17
forum: Server Platforms
---

### Post by ryazkhan on 2009-03-17
I was searching forum for couple of weeks to find a good article about setting freeradius server on ubuntu which will support eap/peap with tls, which is the common way for IEEE 802.1x authentication, either for wireless access point or wired setup. I find lot of comments like freeradius is a beast like LDAP, people were frustrated about setting it up, do not support tls, and so on..

After doing lot of research and googling about its setup I was finally able to set it up with eap/peap and tls support. I would like to share this with you guys because there are lot of people out there struggling for freeradius setup so my pain will be gain for someone hopefully ;), so lets start

_Assumptions:_
1. I am assuming that you have already install Ubuntu 8.04.2 (it should not matter though but mine is 8.04.2 server so)
2. I am assuming that you have downloaded latest version from [_[COLOR="Blue"]source[/COLOR]_]("http://freeradius.org/download.html")
3. I am assuming that you have already unzipped the package and already moved to unzipped directory.
4. I am assuming that you are working as root
5. I am assuming that you have static IP (not that it matters but it is nice to have static IP for servers)

Okay we are now ready to fight with this beast (freeradius)
We need to make a Debian package from the source we just downloaded and unzipped. We also need lot of libs but I would like to system to tell me what I am missing because we can do that and in that way there are very least chances to fill HDD with unnecessary Junk, this is only my preference you don't have to stick with it.

So try this to make a Debian package, you will get lot of errors. Don't worry we will take care of those error(s)> dpkg-buildpackage -b -uc

Next install all missing libs, the setup is complaining about. You need all of them any way so just install them ahead of time
> apt-get install build-essential libltdl3-dev libpam0g-dev libmysqlclient15-dev libgdbm-dev libldap2-dev libsasl2-dev libiodbc2-dev libkrb5-dev libperl-dev libpcap-dev python-dev snmp libsnmp-dev libpq-dev libssl-dev autotools-dev libtool dpatch dh-make devscripts
Now run the setup again and hopefully it would not spit any error(s) on us this time and it will start to build package(s) we need. At this point mine setup started to make packages> dpkg-buildpackage -b -uc
If the above command was successful we are all set here and we should have some Debian packages in our home directory because by default script puts all package in our home directory.

Now that we have our package we need to install them (or at least what we need). So go ahead and issue this command from your home directory or wherever the packages are. Please replace xxx with your version of freeradius
> dpkg -i freeradius_x.x.x_i386 You would likely get error(s) again about missing openssl etc.. So just install what is missing and we should be all set> apt-get install openssl
Now run the setup again and hopefully you would not get any more error, I did not get any after installing openssl> dpkg -i freeradius_x.x.x_i386That is it folks our FreeRADIUS server is ready, but we need to configure it so we can test it out, we need to setup user(s), password(s) etc.. So now move to freeradius directory > cd /etc/freeradius There is a file called users, we want to edit this first to put our user(s) information in it > cd /etc/freeradiusAnd issue > nano users
Add user on about line 92 (this is just a hint, you can put it on any appropriate place)
```
"rkhan"		Cleartext-Password := "rkhan"
		Reply-Message = "Hello Ryaz, authentication was successfull"

```Yes we are using clear password, you can setup different thing to retrieve user info like MYSQL, LDAP, krb5 or some, but that is not in the scope of this article. Hey if we access password using eap/peap, mschapv2, tls etc we are not sending clear password over the internet or intranet, but yes we are storing in clear text in this setup

That is it now we are ready to test because by default localhost is allowed with secret key of testing123, to see the password edit users clients.conf

So start server in debug mode> freeradius -X You probably have to restart, start, or stop the server before you can use above command.

So when you run in debug mode it should say that ready to process requests the very last line

Open an other terminal and test server by typing > radtest rkhan rkhan localhost 1812 testing123 Now notice on the terminal where server is running in debug mode, you will notice some processes occuring and on your testing terminal you will also get message Access-Accept(Reject is not a good sign) and will display the message Hello Ryaz, authentication was successful.

That is it Server is up and running and ready to serve clients. If you want to allow any other client(s) like your access point etc you need to edit clients file located in freeradius directory
> nano /etc/freeradius/clients.conf

Enjoy it !

Configure you access point etc and have fun with your new radius

You can always access this article from [[COLOR="Blue"]_my website_[/COLOR]]("http://ezetech.selfip.info/pages/howtos.php")

---

### Post by Highl1 on 2009-06-18
thanks a lot, this worked like a charm for me, and I finally managed to setup FreeRadius with PEAP support

---

### Post by ryazkhan on 2009-06-23
> **Highl1 said:**
> thanks a lot, this worked like a charm for me, and I finally managed to setup FreeRadius with PEAP support

My pleasure, glad it worked

---

### Post by BIL100 on 2009-10-22
Hey ryazkhan,

Thanks for posting this!

I am going to install freeradius version 2.1.7 and before doing anything wrong i want
to ask you if i have to Install the LAMP server on the Ubuntu server 8.04.2.

Do i also need a SQL database? I have 800+ users. I am going to configure the Radius
server to my Firewall Box.Any-trusted Internal network Users will be forwarded to the Radius
server.

Awaiting for your good suggestions.

Bill

---

### Post by Freeradub on 2009-11-19
Thanks Ryaz Khan, for this informative post.
I am installing freeradius-server-2.1.7 and have all the pre-requisites installed.
but after launching the command dpkg-buildpackage -b -uc, configuration and compilation goes through and the system outputs an error during linkage pasted below.
can you provide inputs on how to fix the same. Appreciate your response.

Thanks!

libtool: link: rm -f .libs/radiusd.nm .libs/radiusd.nmS .libs/radiusd.nmT
libtool: link: (cd .libs && gcc -Wall -g -O2 -c -fno-builtin "radiusdS.c")
libtool: link: rm -f ".libs/radiusdS.c" ".libs/radiusd.nm" ".libs/radiusd.nmS" ".libs/radiusd.nmT"
libtool: link: gcc .libs/radiusdS.o -Wl,-Bsymbolic-functions -o .libs/radiusd .libs/acct.o .libs/auth.o .libs/client.o .libs/conffile.o .libs/crypt.o .libs/exec.o .libs/files.o .libs/listen.o .libs/log.o .libs/mainconfig.o .libs/modules.o .libs/modcall.o .libs/radiusd.o .libs/stats.o .libs/session.o .libs/threads.o .libs/util.o .libs/valuepair.o .libs/version.o .libs/xlat.o .libs/event.o .libs/realms.o .libs/evaluate.o .libs/vmps.o .libs/detail.o -Wl,--export-dynamic  /home/anite/Desktop/test/freeradius-server-2.1.7/src/lib/.libs/libfreeradius-radius.so -lnsl -lresolv -lpthread -lcrypt /usr/lib/libltdl.so -lssl -lcrypto  -Wl,-rpath -Wl,/usr/lib/freeradius
.libs/modules.o: In function `setup_modules':
/home/Desktop/test/freeradius-server-2.1.7/src/main/modules.c:1333: undefined reference to `lt_preloaded_symbols'
collect2: ld returned 1 exit status
make[5]: *** [radiusd] Error 1
make[5]: Leaving directory `/home/Desktop/test/freeradius-server-2.1.7/src/main'
make[4]: *** [common] Error 2
make[4]: Leaving directory `/home/Desktop/test/freeradius-server-2.1.7/src'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/Desktop/test/freeradius-server-2.1.7/src'
make[2]: *** [common] Error 2
make[2]: Leaving directory `/home/Desktop/test/freeradius-server-2.1.7'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/Desktop/test/freeradius-server-2.1.7'
make: *** [build-arch-stamp] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2

---


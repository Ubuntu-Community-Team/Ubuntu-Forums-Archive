---
title: "asterisk+freepbx on server"
date: 2013-09-19
forum: Server Platforms
---

### Post by atux on 2013-09-19
i am moving from an older asterisk version to a new server running 12.04 server edition with asterisk and freepbx.

after googling i came across the [https://github.com/jonathan-roper/Ballistic-PBX/blob/master/install-ballistic-pbx.sh](https://github.com/jonathan-roper/Ballistic-PBX/blob/master/install-ballistic-pbx.sh) and i would like to get it to run the process of installation.
_**problem 1:**_
atux@server:/usr/src$ wget [https://github.com/jonathan-roper/Ballistic-PBX/blob/master/install-ballistic-pbx.sh](https://github.com/jonathan-roper/Ballistic-PBX/blob/master/install-ballistic-pbx.sh)                                          --2013-09-19 21:12:55--  [https://github.com/jonathan-roper/Ballistic-PBX/blob/master/install-ballistic-pbx.sh](https://github.com/jonathan-roper/Ballistic-PBX/blob/master/install-ballistic-pbx.sh)
Resolving github.com... 192.30.252.129
Connecting to github.com|192.30.252.129|:443... connected.
ERROR: cannot verify github.com&#946;s certificate, issued by &#946;/C=US/O=DigiCert Inc/OU=www.digicert.com/CN=DigiCert High Assurance EV CA-1&#946;
                                                                                                                                        Unable to locally verify the issuer&#946;s authority.
To connect to github.com insecurely, use &#946;--no-check-certificate&#946;.
atux@server:/usr/src$

If i put the --no-check-certicate option i do get the file.

_**Problem 2**_
then i do chmod +x filename   (as sudo) and as sudo i am trying to execute it.

atux@server:/usr/src# ./install-ballistic-pbx.sh
./install-ballistic-pbx.sh: line 4: syntax error near unexpected token `newline'
./install-ballistic-pbx.sh: line 4: `<!DOCTYPE html>'
atux@server:/usr/src#



if i open the install-ballistic-pbx.sh it has endless of HTML coding

i do need some help since i am lost with this script.

---

### Post by volkswagner on 2013-09-20
I suggest checking out [freedoh.net]("http://www.freedoh.net/freedoh.html")

---


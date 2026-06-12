---
title: "Error in setting up CA during OpenVPN configuration on Ubuntu Server 12.04 x64"
date: 2012-06-10
forum: Server Platforms
---

### Post by Nick_NS on 2012-06-10
I have been trying to set up OpenVPN on my fresh installation of Ubuntu Server 12.04. Following the instructions on [https://help.ubuntu.com/12.04/serverguide/openvpn.html#openvpn-pki-setup](https://help.ubuntu.com/12.04/serverguide/openvpn.html#openvpn-pki-setup) I kept running into the errors when attempting to execute:
```

Nicholas@server:/etc/openvpn/easy-rsa$ source vars
**************************************************************
  No /etc/openvpn/easy-rsa/openssl.cnf file could be found
  Further invocations will fail
**************************************************************

```
I'll be the first to admit I'm a relative n00b when it comes to the CLI so this explanation may seem obvious to some but I figure there will probably be others like me with a similar issue. This took me several hours to figure out and I hope I'll be able to save someone this trouble.

I noticed there were several versions of openssl.cnf in the directory. Running```
dpkg -s openssl
``` I determined my version was 1.0.1 so modified the following line in the *vars* file to the closest match:
```

# This variable should point to
# the openssl.cnf file included
# with easy-rsa.
export KEY_CONFIG=`$EASY_RSA/**openssl-1.0.0.cnf** $EASY_RSA`
```
This ended up giving me a new error:```
Nicholas@server:/etc/openvpn/easy-rsa$ source vars
-bash: /etc/openvpn/easy-rsa/openssl-1.0.0.cnf: Permission denied

```
I should note that I ran ```
chown -R Nicholas /etc/openvpn/easy-rsa/
``` after copying the easy-rsa folder to /etc/openvpn/ in order to avoid the need for sudo all the time. 

At this point I tried many different methods for trying to get past this error including allowing the openssl-1.0.0.cnf file to be executable, running the command with sudo. Nothing worked. I had almost given up and was going to generate the CA and related files using my client laptop running Windows 7 when I noticed that in the Windows version, part of the *vars* file was different. 

Modifying the vars file on my server to remove the single quotes and the second $EASY_RSA reference allowed the source vars command to complete successfully and I was able to continue the setup without incident.
```

# This variable should point to
# the openssl.cnf file included
# with easy-rsa.
export KEY_CONFIG=$EASY_RSA/openssl-1.0.0.cnf #<-This format works

```

---

### Post by omghax on 2012-11-18
Thank you so much, this fixed everything! :KS

---

### Post by Virus666 on 2013-01-17
Thank you sir! That solved my problem in Linux Mint 13 Maya i386 Mate.

---

### Post by camurgo on 2013-01-20
I was about to try the above workaround... but before that I decided to simply try the following:

cd /etc/openvpn/easy-rsa
sudo ln -s openssl-1.0.0.cnf openssl.cnf

And it worked perfectly.

(This created a link to openssl-1.0.0.cnf with the name openssl.cnf in the same directory)

---

### Post by YLearn on 2013-02-13
Just stumbled on this looking for another issue and while the OP's solution and Cameigons solution will both allow the variables to be set, I did want to point out where the problem exists for those interested in learning.

The original line in the vars file contained backticks (aka backward quotes, backquotes,  etc), not single quotes.  Backticks are used to execute enclosed  commands and substitiute the output into that location.

What this line should do is run the "whichopensslcnf" script, and that should  output the correct openssl*.cnf file for the installed version of  OpenSSL (prepended with the path $EASY_RSA).  If it fails to match the  version of OpenSSL, it looks for a default openssl.cnf file.

So, the problem is in the "whichopensslcnf" script.  Odds are on these systems, they would get output similar to one of my *nix machines:```
[me@localhost place]$ openssl version
OpenSSL 1.0.0-fips 29 Mar 2010
```Looking in the original "whichopensslcnf" script, I find this:```
elif $OPENSSL version | grep -E "1\.0\.([[:digit:]][[:alnum:]])" > /dev/null; then
                cnf="$1/openssl-1.0.0.cnf"
```This doesn't match my OpenSSL version output on the system because it doesn't allow for the dash ("-"). 

A side note: The parentheses really don't do anything in that line at present.  My guess would be that they are a "relic" of old code in that line or an allowance for an OR match in the future.

If you replace that piece of code with the below, it should work as intended (leave the parentheses if you want):```
elif $OPENSSL version | grep -E "1\.0\.[[:digit:]]-{0,1}[[:alnum:]]" > /dev/null; then
                cnf="$1/openssl-1.0.0.cnf"
```This simply adds to allow 0 or 1 occurances of a dash ("-") between the third digit and the next alphanumeric character and it will now match my OpenSSL version, which in turn allows the script to finish without error and set the variable with my "openssl*.cnf" file correctly.

---


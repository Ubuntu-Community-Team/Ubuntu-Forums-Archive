---
title: "Openvpn istallation\configuration help"
date: 2010-04-03
forum: Server Platforms
---

### Post by jfmanamtr on 2010-04-03
I am trying to install openvpn on my server(ubuntu Server 9.10) so that I can grant access to it for my fiance outside the home. I used the instructions in the documentation section for VPN under the server section ([link]("https://help.ubuntu.com/9.10/serverguide/C/openvpn.html")). I did the install using 'sudo apt-get install openvpn'. Inside /etc/openvpn, I only see a file called 'update-resolv-conf'. I then issue the next 2 commands, & then the rest of the instructions in the guide seem to fail. I really would like to make this work. So, any ideas on what I am doing wrong? Maybe you have a link to a better installation & configuration guide? Thanks for all your help ahead of time!!

~John

---

### Post by gombadi on 2010-04-03
> 
I used the instructions in the documentation section for VPN under the server section (link). I did the install using 'sudo apt-get install openvpn'. Inside /etc/openvpn, I only see a file called 'update-resolv-conf'. I then issue the next 2 commands, & then the rest of the instructions in the guide seem to fail.


So you issue the next two commands (mkdir and cp) with no problems and from then you have problems?
The following command is to edit the /etc/openvpn/easy-rsa/vars file.

What error do you get when you edit this file?

---

### Post by jfmanamtr on 2010-04-03
Sorry, my mistake. I can edit the file without troubles. I start having issues here:

```
cd /etc/openvpn/easy-rsa/easy-rsa
source vars
./clean-all
./build-dh
./pkitool --initca
./pkitool --server server
cd keys
openvpn --genkey --secret ta.key
sudo cp server.crt server.key ca.crt dh1024.pem ta.key /etc/openvpn/
```First thing is that When I tell it 'source ./vars', I can't tell if it works. Then I issue ./clean-all & get told:

```
Please source the vars script first (i.e. "source ./vars")
Make sure you have edited it to reflect your configuration.

```I have edited them though. I am not sure what is going on exactly. Any ideas?

This is the vars file:
```
# easy-rsa parameter settings

# NOTE: If you installed from an RPM,
# don't edit this file in place in
# /usr/share/openvpn/easy-rsa --
# instead, you should copy the whole
# easy-rsa directory to another location
# (such as /etc/openvpn) so that your
# edits will not be wiped out by a future
# OpenVPN package upgrade.

# This variable should point to
# the top level of the easy-rsa
# tree.
export EASY_RSA="`pwd`"

#
# This variable should point to
# the requested executables
#
export OPENSSL="openssl"
export PKCS11TOOL="pkcs11-tool"
export GREP="grep"

# This variable should point to
# the openssl.cnf file included
# with easy-rsa.
export KEY_CONFIG=`$EASY_RSA/whichopensslcnf $EASY_RSA`

# Edit this variable to point to
# your soon-to-be-created key
# directory.
#
# WARNING: clean-all will do
# a rm -rf on this directory
# so make sure you define
# it correctly!
export KEY_DIR="$EASY_RSA/keys"

# Issue rm -rf warning
echo NOTE: If you run ./clean-all, I will be doing a rm -rf on $KEY_DIR

# PKCS11 fixes
export PKCS11_MODULE_PATH="dummy"
export PKCS11_PIN="dummy"

# Increase this to 2048 if you
# are paranoid.  This will slow
# down TLS negotiation performance
# as well as the one-time DH parms
# generation process.
export KEY_SIZE=1024

# In how many days should the root CA key expire?
export CA_EXPIRE=3650

# In how many days should certificates expire?
export KEY_EXPIRE=3650

# These are the default values for fields
# which will be placed in the certificate.
# Don't leave any of these fields blank.
export KEY_COUNTRY="US"
export KEY_PROVINCE="NC"
export KEY_CITY="Charlotte"
export KEY_ORG="MorrenInc"
export KEY_EMAIL="jmorren@gmail.com"
```

~John

---

### Post by dipeshmehta on 2010-04-04
You may check this link: [http://www.openvpn.net/index.php/open-source/documentation/howto.html](http://www.openvpn.net/index.php/open-source/documentation/howto.html)

It's very nice step-by-step howto

Dipesh

---

### Post by jfmanamtr on 2010-04-04
Thanks for the link. I don't know if it is the instructions or not, but these also get me to the same place. After issuing the ./clean-all, it tells me to make sure I edit the vars file that I have edited. Any ideas on what I could be doing wrong?
 
~John

---

### Post by spynappels on 2010-04-04
Try using 
```
source ./vars
```

the dot slash is important. When you run this, it will tell you to run ./clean-all but it will warn you that this will basically wipe out any keys in your keys folder.

---

### Post by doogy2004 on 2010-04-04
I use OpenVPN AS, it is easy to install and setup, the client is also easy to get installed and working.

[http://openvpn.net/index.php/access-server/access-server-overview.html](http://openvpn.net/index.php/access-server/access-server-overview.html)

---

### Post by jfmanamtr on 2010-04-04
Ok. So, I just installed OpenVPN AS & it is up in running. I think the entire configuration too like 5 minutes. Thanks for all your help!

~John

---


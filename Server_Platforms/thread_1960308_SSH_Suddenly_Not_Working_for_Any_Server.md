---
title: "SSH Suddenly Not Working for Any Server"
date: 2012-04-17
forum: Server Platforms
---

### Post by coronacolada on 2012-04-17
Hello,

I've had my system up and running for almost a year now with hardly any modifications. Suddenly, I'm unable to SSH into anything at all. 


The server itself does not matter. I have tried three different servers with three different operating systems. None of them work. As soon as I am successfully logged in, Write failed: broken pipe shows up. 

There is nothing in ```
syslog
```. It merely shows "session opened by Tom", followed immediately by "session closed by Tom".

I have run ```
mtr
```, and show 0 packet loss or other anomalies when pinging my primary dev server. It also doesn't matter whether I'm wired or wireless. 

I have tried ```
apt-get install --reinstall openssh
```, but to no avail.

Below is the output of both ssh -v and ssh -vvv. I have a running thread on unix.stackexchange.com as well, if you prefer that forum.

This has made me utterly unable to do much of my work. Any help would be appreciated.

Running 11.04.

ssh -v output:

```
~ >> ssh -v clearpoint@turnleftllc.com
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to turnleftllc.com [72.167.39.231] port 22.
debug1: Connection established.
debug1: identity file /home/tom/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/tom/.ssh/id_rsa-cert type -1
debug1: identity file /home/tom/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: identity file /home/tom/.ssh/id_dsa-cert type -1
debug1: identity file /home/tom/.ssh/id_ecdsa type -1
debug1: identity file /home/tom/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.5
debug1: match: OpenSSH_5.5 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-1ubuntu3
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA 87:81:14:42:23:b7:5b:94:eb:a9:f5:25:e0:e9:1a:0b
debug1: Host 'turnleftllc.com' is known and matches the RSA host key.
debug1: Found key in /home/tom/.ssh/known_hosts:9
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic,password
debug1: Next authentication method: gssapi-keyex
debug1: No valid Key exchange context
debug1: Next authentication method: gssapi-with-mic
debug1: Unspecified GSS failure.  Minor code may provide more information
Credentials cache file '/tmp/krb5cc_1000' not found

debug1: Unspecified GSS failure.  Minor code may provide more information
Credentials cache file '/tmp/krb5cc_1000' not found

debug1: Unspecified GSS failure.  Minor code may provide more information


debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/tom/.ssh/id_rsa
debug1: Server accepts key: pkalg ssh-rsa blen 279
debug1: read PEM private key done: type RSA
debug1: Authentication succeeded (publickey).
Authenticated to turnleftllc.com ([72.167.39.231]:22).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
Write failed: Broken pipe
```

The last portion of ssh -vvv output (using a different server):

```
debug2: we did not send a packet, disable method
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/tom/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,gssapi-with-mic,password
debug1: Offering DSA public key: /home/tom/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,gssapi-with-mic,password
debug1: Trying private key: /home/tom/.ssh/id_ecdsa
debug3: no such identity: /home/tom/.ssh/id_ecdsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
koenig@50.57.55.206's password: 
debug3: packet_send2: adding 48 (len 63 padlen 17 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
Authenticated to 50.57.55.206 ([50.57.55.206]:22).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: fd 3 setting TCP_NODELAY
debug3: packet_set_tos: set IP_TOS 0x10
debug2: channel 0: request pty-req confirm 1
debug1: Sending environment.
debug3: Ignored env ORBIT_SOCKETDIR
debug3: Ignored env SSH_AGENT_PID
debug3: Ignored env TERM
debug3: Ignored env SHELL
debug3: Ignored env XDG_SESSION_COOKIE
debug3: Ignored env WINDOWID
debug3: Ignored env GNOME_KEYRING_CONTROL
debug3: Ignored env GTK_MODULES
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env LIBGL_DRIVERS_PATH
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env USERNAME
debug3: Ignored env DEFAULTS_PATH
debug3: Ignored env XDG_CONFIG_DIRS
debug3: Ignored env PATH
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env PWD
debug3: Ignored env GDM_KEYBOARD_LAYOUT
debug3: Ignored env GNOME_KEYRING_PID
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env GDM_LANG
debug3: Ignored env MANDATORY_PATH
debug3: Ignored env UBUNTU_MENUPROXY
debug3: Ignored env PS1
debug3: Ignored env GDMSESSION
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env LANGUAGE
debug3: Ignored env LOGNAME
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env WINDOWPATH
debug3: Ignored env DISPLAY
debug3: Ignored env LESSCLOSE
debug3: Ignored env COLORTERM
debug3: Ignored env XAUTHORITY
debug3: Ignored env _
debug2: channel 0: request shell confirm 1
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
Write failed: Broken pipe
```

---

### Post by nothingspecial on 2012-04-18
*Thread moved to **Server Platforms**.*

---

### Post by webservervideos on 2012-04-18
are you using keys that have an expiry date? You said it has almost been a year...maybe they expired? Perhaps you disabled login via password and that is killing your password attempts?

---


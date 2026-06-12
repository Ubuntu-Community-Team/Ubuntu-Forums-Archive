---
title: "remote scp stopped work for me.  Help"
date: 2008-05-11
forum: Security
---

### Post by wbrown on 2008-05-11
Greetings: 

I use scp to copy / backup a set of database files between servers in my setup.  This has been working just fine but broke on 4/25/2008 and I haven't been able to get it working

this is the error message I get

server.root#> scp myFile nonRoot@myOtherHost:/nonRootPermission/path

bash: scp: command not found
lost connection

I am attempting as root to scp into the remote server as a non root user and copy the files to a directory that the non root user has permissions on.  This has worked previously without issue.  The remote machine was upgraded to 8.04 recently.  Could that have caused this issue?  Does anyone here know how to fix it?  I suspect it may be a config setting in /etc/ssh/ but I haven't been able to figure out which.  

Thanks for looking at this.

Bill

---

### Post by Monicker on 2008-05-11
Strange.  Do other commands, such as ssh, work?  ssh and scp are both part of the openssh-client package?

Could it be a path problem? What are the results of the following commands?

```
locate scp
which scp
echo $PATH
```

---

### Post by wbrown on 2008-05-11
Greetings Monicker:

I am able to run ssh and scp from the remote host to the other host.  So it does work the other way.  Here is what I get from the commands you suggested. 

$ locate scp
/lib/iptables/libipt_dscp.so
/lib/modules/2.6.22-10-generic/kernel/drivers/hwmon/fscpos.ko
/lib/modules/2.6.22-10-generic/kernel/net/netfilter/xt_dscp.ko
/lib/modules/2.6.22-12-generic/kernel/drivers/hwmon/fscpos.ko
/lib/modules/2.6.22-12-generic/kernel/net/netfilter/xt_dscp.ko
/lib/modules/2.6.22-12-rt/kernel/drivers/hwmon/fscpos.ko
/lib/modules/2.6.22-12-rt/kernel/net/netfilter/xt_dscp.ko
/lib/modules/2.6.22-13-generic/kernel/drivers/hwmon/fscpos.ko
/lib/modules/2.6.22-13-generic/kernel/net/netfilter/xt_dscp.ko
/lib/modules/2.6.22-13-rt/kernel/drivers/hwmon/fscpos.ko
/lib/modules/2.6.22-13-rt/kernel/net/netfilter/xt_dscp.ko
/lib/modules/2.6.22-14-rt/kernel/drivers/hwmon/fscpos.ko
/lib/modules/2.6.22-14-rt/kernel/net/netfilter/xt_dscp.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/hwmon/fscpos.ko
/lib/modules/2.6.24-16-generic/kernel/net/netfilter/xt_dscp.ko
/lib/modules/2.6.24-16-rt/kernel/drivers/hwmon/fscpos.ko
/lib/modules/2.6.24-16-rt/kernel/net/netfilter/xt_dscp.ko
/lib/modules/2.6.24-17-generic/kernel/drivers/hwmon/fscpos.ko
/lib/modules/2.6.24-17-generic/kernel/net/netfilter/xt_dscp.ko
/lib/modules/2.6.24-17-rt/kernel/drivers/hwmon/fscpos.ko
/lib/modules/2.6.24-17-rt/kernel/net/netfilter/xt_dscp.ko
/usr/bin/scp
/usr/include/linux/netfilter/xt_dscp.h
/usr/include/linux/netfilter_ipv4/ipt_dscp.h
/usr/lib/liblscp.so.5
/usr/lib/liblscp.so.5.0.0
/usr/lib/cups/filter/commandtoescpx
/usr/lib/cups/filter/rastertoescpx
/usr/lib/gutenprint/5.0.2/modules/print-escp2.la
/usr/lib/gutenprint/5.0.2/modules/print-escp2.so
/usr/lib/kde3/kdeprint_tool_escputil.la
/usr/lib/kde3/kdeprint_tool_escputil.so
/usr/share/apps/kdeprint/tools/escputil.desktop
/usr/share/cupsddk/include/escp.h
/usr/share/doc/liblscp2
/usr/share/doc/cupsddk/help/man-rastertoescpx.html
/usr/share/doc/liblscp2/changelog.Debian.gz
/usr/share/doc/liblscp2/changelog.gz
/usr/share/doc/liblscp2/copyright
/usr/share/foomatic/db/source/driver/escpage.xml
/usr/share/ghostscript/8.61/lib/escp_24.src
/usr/share/ghostscript/8.61/lib/gs_dscp.ps
/usr/share/man/man1/commandtoescpx.1.gz
/usr/share/man/man1/rastertoescpx.1.gz
/usr/share/man/man1/scp.1.gz
/usr/share/mime/audio/x-scpls.xml
/usr/share/mimelnk/audio/x-scpls.desktop
/usr/share/webmin/blue-theme/escputil
/usr/share/webmin/blue-theme/escputil/images
/usr/share/webmin/blue-theme/escputil/images/icon.gif
/usr/share/webmin/caldera/escputil
/usr/share/webmin/caldera/escputil/images
/usr/share/webmin/caldera/escputil/images/icon.gif
/usr/share/webmin/proc/help/scpu.ca.html
/usr/share/webmin/proc/help/scpu.es.html
/usr/share/webmin/proc/help/scpu.fr.html
/usr/share/webmin/proc/help/scpu.html
/usr/share/webmin/proc/help/scpu.hu.html
/usr/share/webmin/proc/help/scpu.pl.html
/usr/share/webmin/proc/help/scpu.sv.html
/usr/share/webmin/proc/help/scpu.zh_TW.Big5.html
/usr/share/webmin/proc/help/scpu.zh_TW.UTF-8.html
/usr/src/linux-headers-2.6.22-10/include/linux/netfilter/xt_dscp.h
/usr/src/linux-headers-2.6.22-10/include/linux/netfilter_ipv4/ipt_dscp.h
/usr/src/linux-headers-2.6.22-10-generic/include/config/netfilter/xt/match/dscp.h
/usr/src/linux-headers-2.6.22-10-generic/include/config/netfilter/xt/target/dscp.h
/usr/src/linux-headers-2.6.22-10-generic/include/config/sensors/fscpos.h
/usr/src/linux-headers-2.6.22-13/include/linux/netfilter/xt_dscp.h
/usr/src/linux-headers-2.6.22-13/include/linux/netfilter_ipv4/ipt_dscp.h
/usr/src/linux-headers-2.6.22-13-generic/include/config/netfilter/xt/match/dscp.h
/usr/src/linux-headers-2.6.22-13-generic/include/config/netfilter/xt/target/dscp.h
/usr/src/linux-headers-2.6.22-13-generic/include/config/sensors/fscpos.h
/usr/src/linux-headers-2.6.24-17/include/linux/netfilter/xt_dscp.h
/usr/src/linux-headers-2.6.24-17/include/linux/netfilter_ipv4/ipt_dscp.h
/usr/src/linux-headers-2.6.24-17-generic/include/config/netfilter/xt/match/dscp.h
/usr/src/linux-headers-2.6.24-17-generic/include/config/netfilter/xt/target/dscp.h
/usr/src/linux-headers-2.6.24-17-generic/include/config/sensors/fscpos.h
/var/lib/dpkg/info/liblscp.list
/var/lib/dpkg/info/liblscp.postrm
/var/lib/dpkg/info/liblscp2.list
/var/lib/dpkg/info/liblscp2.md5sums
/var/lib/dpkg/info/liblscp2.postinst
/var/lib/dpkg/info/liblscp2.postrm
/var/lib/dpkg/info/liblscp2.shlibs

$ which scp
/usr/bin/scp

$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

It seems like the /usr/bin/scp command should be in the bath based on the PATH output.  I also ran 'sudo dpkg-reconfigure openssh-client' but that had no effect.  Do you know of anything else I can try? 

Thanks.
Bill

---

### Post by Monicker on 2008-05-11
Do you have an alias called scp which might be calling it in a specific way? That would take precedence over your path.

What does this show?

```
alias
```

---

### Post by wbrown on 2008-05-12
I get this from the alias command:

$ alias
alias ls='ls --color=auto'

some mailing list threads I've looked at over the internet suggest that the ssh server may not have the path to scp compiled in.  

Thanks for you suggestions / help.  Let me know if you think of anything else.

---

### Post by Monicker on 2008-05-12
But you had used scp for that other host previously, correct?  You could check /var/log/auth.log for entries about ssh.  Also try scp with the -v option, and see if it spits out more detail.

Aside from that, I don't know what might be happening.

---

### Post by wbrown on 2008-05-12
Greetings Monicker:  

Here is the output I get from running scp -v.  There is more debug information here including the 127 exit error code but I'm not sure what that means.  I will try looking it up on the web to see if it is something specific that can help resolve this. I also notice that there is a -t option added but I haven't found out what that is.  Thanks again for looking at this. 


# scp -v myFile nonRoot@myOtherHost:/nonRootPermission/path
Executing: program /usr/bin/ssh myOtherHost, user myUser, command scp -v -t
 /nonRootPermission/path
OpenSSH_4.3p2 Debian-8ubuntu1.2, OpenSSL 0.9.8c 05 Sep 2006
debug1: Connecting to myOtherHost [71.194.171.185] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/identity type -1
debug1: identity file /root/.ssh/id_rsa type 1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1

debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'myOtherHost' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/identity
debug1: Offering public key: /root/.ssh/id_rsa
debug1: Server accepts key: pkalg ssh-rsa blen 277
debug1: read PEM private key done: type RSA
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending command: scp -v -t /nonRootPermission/path
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
bash: scp: command not found
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
debug1: fd 1 clearing O_NONBLOCK
debug1: Transferred: stdin 0, stdout 0, stderr 0 bytes in 0.2 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.0
debug1: Exit status 127
lost connection
#

---

### Post by Monicker on 2008-05-12
Out of curiousity, I renamed scp on my laptop,and then tried to scp a file over to it.  I get the same message as you:

```
bash: scp: command not found
```

So it seems that you should definitely look at the the remote host.

---

### Post by wbrown on 2008-05-12
Ok. So I reinstalled openssh-client and openssh-server on the remote host and added ~/.ssh/environment with either of these in it: 

PATH=/usr/bin/scp:$PATH:/usr/bin/scp

or

PATH=/usr/bin:$PATH:/usr/bin

but still no luck yet.  From the debut output, is it possible that the remote version of of open ssh
 
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1 

doesn't have /usr/bin in the path? 

Are others running remote scp from  7.04 (fiesty) to a remote 8.04 (hardy)? 

Thanks.
Bill

---

### Post by DougMcNutt on 2008-09-20
Please excuse the format of this. I simply don't understand all of the icons.

But scp has also stopped working for me at about the same time. I have been fighting it for the last two days. A debug line referred to SELinux and I went ahead and installed it and set it to permissive but it didn't help.

My problem is scp'ing from Mac OS 10.3.9 to Linux but I have exactly the same problem transferring from another Hardy Heron box.  The target file is reported as a "read error" and scp quite leaving the shell from which it was requested in an open state. I have to hit a return manually to get a prompt.

I can use ssh to get a shell on the Linux host and it works fine. I can use cat >> somefile and transfer text files using copy and paste with a CONTROL-D at the end so I'm pretty sure that ssh is NOT the problem. It's only scp.

I can transfer files if I execute scp from a shell on the Hardy Heron box and I can also use the curl tool to transfer via ftp but I donwannadodat.

I'd like to enclose a debug list with one of those scrollable windows but I donno how. I'll try just pasting the contents of a text file which includes two parts. One is the report from a private instance of the sshd I created on the Linux box. The other is the result of an scp with the -vvv option.  Look for the debug2 * read failed line.I can't get away from it!


Running scp request from a terminal session on Mac OS 10.3.9

[~/.ssh]% scp -vvv -i $HOME/.ssh/id_rsa_u -P 4000 DUAT_080630 Mars:
Executing: program /usr/bin/ssh host Mars, user (unspecified), command scp -v -t .
OpenSSH_4.5p1, OpenSSL 0.9.7l 28 Sep 2006
debug1: Reading configuration data /Users/doug/.ssh/config
debug1: Applying options for Mars
debug1: Reading configuration data /etc/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to Mars [192.168.1.19] port 4000.
debug1: Connection established.
debug3: Not a RSA1 key file /Users/doug/.ssh/id_rsa_u.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /Users/doug/.ssh/id_rsa_u type 1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.5
debug2: fd 3 setting O_NONBLOCK
debug1: An invalid name was supplied
Configuration file does not specify default realm

debug1: An invalid name was supplied
Configuration file does not specify default realm

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_init: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_init: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 135/256
debug2: bits set: 505/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: put_host_port: [192.168.1.19]:4000
debug3: put_host_port: [mars]:4000
debug3: check_host_in_hostfile: filename /Users/doug/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh_known_hosts
debug3: check_host_in_hostfile: filename /Users/doug/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh_known_hosts
debug1: checking without port identifier
debug3: check_host_in_hostfile: filename /Users/doug/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 44
debug3: check_host_in_hostfile: filename /Users/doug/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 44
debug1: Host 'mars' is known and matches the RSA host key.
debug1: Found key in /Users/doug/.ssh/known_hosts:44
debug1: found matching key w/out port
debug2: bits set: 459/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /Users/doug/.ssh/id_rsa (0x322d20)
debug2: key: /Users/doug/.ssh/id_dsa (0x33f1f0)
debug2: key: /Users/doug/.ssh/id_rsa_u (0x302910)
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /Users/doug/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Remote: Adding to environment: SSH_DOUG=RSA_MacOS_10.3.9
debug1: Server accepts key: pkalg ssh-rsa blen 149
debug2: input_userauth_pk_ok: fp 15:56:21:9e:7d:10:88:3d:08:d3:62:8f:5d:0e:48:d9
debug3: sign_and_send_pubkey
debug1: Remote: Adding to environment: SSH_DOUG=RSA_MacOS_10.3.9
debug1: Authentication succeeded (publickey).
debug2: fd 4 setting O_NONBLOCK
debug2: fd 5 setting O_NONBLOCK
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug1: Sending command: scp -v -t .
debug2: channel 0: request exec confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel 0: rcvd adjust 2097152
debug2: channel 0: rcvd ext data 166
debug3: PAM: opening session
debug3: PAM: sshpam_store_conv called with 1 messages
debug1: PAM: reinitializing credentials
debug1: permanently_set_uid: 1001/1003
debug2: channel 0: written 166 to efd 6
debug2: channel 0: rcvd ext data 146
debug2: channel 0: rcvd ext data 243
debug2: channel 0: rcvd ext data 578
Welcome to Mars
debug1: SELinux support enabled
debug3: ssh_selinux_setup_exec_context: setting execution context
debug3: ssh_selinux_setup_exec_context: done
debug1: Unable to open session: An SELinux policy prevents this sender from sending this message to this recipient (rejected message had interface "org.freedesktop.DBus" member "Hello" error name "(unset)" destination "org.freedesktop.DBus")
debug3: Copy environment: PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
debug3: Copy environment: LANGUAGE=en_US:en
debug3: Copy environment: LANG=en_US.UTF-8
Environment:
  USER=doug
  LOGNAME=doug
  HOME=/home/doug
  PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
  MAIL=/var/mail/doug
  SHELL=/bin/tcsh
  SSH_DOUG=RSA_MacOS_10.3.9
  SSH_CLIENT=192.168.1.11 50032 4000
  SSH_CONNECTION=192.168.1.11 50032 192.168.1.19 4000
  LANGUAGE=en_US:en
  LANG=en_US.UTF-8
debug3: channel 0: close_fds r -1 w -1 e -1 c -1
debug2: channel 0: written 967 to efd 6
debug2: channel 0: read<=0 rfd 4 len 0
debug2: channel 0: read failed
debug2: channel 0: close_read
debug2: channel 0: input open -> drain
debug2: channel 0: ibuf empty
debug2: channel 0: send eof
debug2: channel 0: input drain -> closed
[~/.ssh]% debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug2: channel 0: rcvd close
debug3: channel 0: will not send data after close
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
debug3: channel 0: status: The following connections are open:
  #0 client-session (t4 r0 i3/0 o3/0 fd -1/-1 cfd -1)

debug3: channel 0: close_fds r -1 w -1 e 6 c -1
debug1: fd 0 clearing O_NONBLOCK
debug1: fd 1 clearing O_NONBLOCK
debug1: Transferred: stdin 0, stdout 0, stderr 0 bytes in 0.3 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.0
debug1: Exit status 0

######  The terminal session has not reverted to a prompt. It will when I enter a return.
[~]% ls -l DUAT*
-rw-r--r--  1 doug  doug   38666 24 May 13:48 DUAT_080524
-rw-r--r--  1 doug  doug  218963 25 May 06:59 DUAT_080525
-rw-r--r--  1 doug  doug   13586 26 May 07:14 DUAT_080526
-rw-r--r--  1 doug  doug   10232 30 Jun 17:51 DUAT_080630
-rw-r--r--  1 doug  doug  106223  1 Jul 05:55 DUAT_080701
[~]% 



daemon report after running a private copy of sshd on Hardy Heron
The daemon was started using an ssh connection in another Mac terminal window.


Mars[~]> sudo /usr/sbin/sshd -ddd -e -k 0 -p 4000 -D -4
[sudo] password for doug: 
debug2: load_server_config: filename /etc/ssh/sshd_config
debug2: load_server_config: done config len = 720
debug2: parse_server_config: config /etc/ssh/sshd_config len 720
debug3: /etc/ssh/sshd_config:5 setting Port 22
debug3: /etc/ssh/sshd_config:9 setting Protocol 2
debug3: /etc/ssh/sshd_config:11 setting HostKey /etc/ssh/ssh_host_rsa_key
debug3: /etc/ssh/sshd_config:12 setting HostKey /etc/ssh/ssh_host_dsa_key
debug3: /etc/ssh/sshd_config:15 setting UsePrivilegeSeparation no
debug3: /etc/ssh/sshd_config:18 setting KeyRegenerationInterval 3600
debug3: /etc/ssh/sshd_config:19 setting ServerKeyBits 768
debug3: /etc/ssh/sshd_config:22 setting SyslogFacility AUTH
debug3: /etc/ssh/sshd_config:23 setting LogLevel INFO
debug3: /etc/ssh/sshd_config:26 setting LoginGraceTime 120
debug3: /etc/ssh/sshd_config:27 setting PermitRootLogin yes
debug3: /etc/ssh/sshd_config:28 setting StrictModes yes
debug3: /etc/ssh/sshd_config:30 setting RSAAuthentication yes
debug3: /etc/ssh/sshd_config:31 setting PubkeyAuthentication yes
debug3: /etc/ssh/sshd_config:35 setting PermitUserEnvironment yes
debug3: /etc/ssh/sshd_config:38 setting IgnoreRhosts yes
debug3: /etc/ssh/sshd_config:40 setting RhostsRSAAuthentication no
debug3: /etc/ssh/sshd_config:42 setting HostbasedAuthentication no
debug3: /etc/ssh/sshd_config:47 setting PermitBlacklistedKeys yes
debug3: /etc/ssh/sshd_config:50 setting PermitEmptyPasswords no
debug3: /etc/ssh/sshd_config:54 setting ChallengeResponseAuthentication no
debug3: /etc/ssh/sshd_config:57 setting PasswordAuthentication yes
debug3: /etc/ssh/sshd_config:69 setting X11Forwarding yes
debug3: /etc/ssh/sshd_config:70 setting X11DisplayOffset 10
debug3: /etc/ssh/sshd_config:71 setting PrintMotd no
debug3: /etc/ssh/sshd_config:72 setting PrintLastLog yes
debug3: /etc/ssh/sshd_config:73 setting TCPKeepAlive yes
debug3: /etc/ssh/sshd_config:80 setting AcceptEnv LANG LC_*
debug3: /etc/ssh/sshd_config:82 setting Subsystem sftp /usr/lib/openssh/sftp-server
debug3: /etc/ssh/sshd_config:84 setting UsePAM yes
debug1: sshd version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug3: Not a RSA1 key file /etc/ssh/ssh_host_rsa_key.
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug3: Not a RSA1 key file /etc/ssh/ssh_host_dsa_key.
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-ddd'
debug1: rexec_argv[2]='-e'
debug1: rexec_argv[3]='-k'
debug1: rexec_argv[4]='0'
debug1: rexec_argv[5]='-p'
debug1: rexec_argv[6]='4000'
debug1: rexec_argv[7]='-D'
debug1: rexec_argv[8]='-4'
debug2: fd 3 setting O_NONBLOCK
debug1: Bind to port 4000 on 0.0.0.0.
Server listening on 0.0.0.0 port 4000.
debug3: fd 4 is not O_NONBLOCK
debug1: Server will not fork when running in debugging mode.
debug3: send_rexec_state: entering fd = 7 config len 720
debug3: ssh_msg_send: type 0
debug3: send_rexec_state: done
debug1: rexec start in 4 out 4 newsock 4 pipe -1 sock 7
debug3: recv_rexec_state: entering fd = 5
debug3: ssh_msg_recv entering
debug3: recv_rexec_state: done
debug2: parse_server_config: config rexec len 720
debug3: rexec:5 setting Port 22
debug3: rexec:9 setting Protocol 2
debug3: rexec:11 setting HostKey /etc/ssh/ssh_host_rsa_key
debug3: rexec:12 setting HostKey /etc/ssh/ssh_host_dsa_key
debug3: rexec:15 setting UsePrivilegeSeparation no
debug3: rexec:18 setting KeyRegenerationInterval 3600
debug3: rexec:19 setting ServerKeyBits 768
debug3: rexec:22 setting SyslogFacility AUTH
debug3: rexec:23 setting LogLevel INFO
debug3: rexec:26 setting LoginGraceTime 120
debug3: rexec:27 setting PermitRootLogin yes
debug3: rexec:28 setting StrictModes yes
debug3: rexec:30 setting RSAAuthentication yes
debug3: rexec:31 setting PubkeyAuthentication yes
debug3: rexec:35 setting PermitUserEnvironment yes
debug3: rexec:38 setting IgnoreRhosts yes
debug3: rexec:40 setting RhostsRSAAuthentication no
debug3: rexec:42 setting HostbasedAuthentication no
debug3: rexec:47 setting PermitBlacklistedKeys yes
debug3: rexec:50 setting PermitEmptyPasswords no
debug3: rexec:54 setting ChallengeResponseAuthentication no
debug3: rexec:57 setting PasswordAuthentication yes
debug3: rexec:69 setting X11Forwarding yes
debug3: rexec:70 setting X11DisplayOffset 10
debug3: rexec:71 setting PrintMotd no
debug3: rexec:72 setting PrintLastLog yes
debug3: rexec:73 setting TCPKeepAlive yes
debug3: rexec:80 setting AcceptEnv LANG LC_*
debug3: rexec:82 setting Subsystem sftp /usr/lib/openssh/sftp-server
debug3: rexec:84 setting UsePAM yes
debug1: sshd version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug3: Not a RSA1 key file /etc/ssh/ssh_host_rsa_key.
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug3: Not a RSA1 key file /etc/ssh/ssh_host_dsa_key.
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: inetd sockets after dupping: 3, 3
Connection from 192.168.1.11 port 50032
debug1: Client protocol version 2.0; client software version OpenSSH_4.5
debug1: match: OpenSSH_4.5 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug2: fd 3 setting O_NONBLOCK
debug1: list_hostkey_types: ssh-rsa,ssh-dss
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST received
debug1: SSH2_MSG_KEX_DH_GEX_GROUP sent
debug2: dh_gen_key: priv key bits set: 133/256
debug2: bits set: 459/1024
debug1: expecting SSH2_MSG_KEX_DH_GEX_INIT
debug2: bits set: 505/1024
debug1: SSH2_MSG_KEX_DH_GEX_REPLY sent
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: KEX done
debug1: userauth-request for user doug service ssh-connection method none
debug1: attempt 0 failures 0
debug3: Trying to reverse map address 192.168.1.11.
debug2: parse_server_config: config reprocess config len 720
debug2: input_userauth_request: setting up authctxt for doug
debug1: PAM: initializing for "doug"
debug1: PAM: setting PAM_RHOST to "earth"
debug1: PAM: setting PAM_TTY to "ssh"
debug2: input_userauth_request: try method none
Failed none for doug from 192.168.1.11 port 50032 ssh2
debug1: userauth-request for user doug service ssh-connection method publickey
debug1: attempt 1 failures 1
debug2: input_userauth_request: try method publickey
debug1: test whether pkalg/pkblob are acceptable
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-1024
debug1: temporarily_use_uid: 1001/1003 (e=0/0)
debug1: trying public key file /home/doug/.ssh/authorized_keys
debug3: secure_filename: checking '/home/doug/.ssh'
debug3: secure_filename: checking '/home/doug'
debug3: secure_filename: terminating check at '/home/doug'
debug2: key_type_from_name: unknown key type 'environment="SSH_DOUG=RSA_MacOS_9.1"'
debug3: key_read: missing keytype
debug2: user_key_allowed: check options: 'environment="SSH_DOUG=RSA_MacOS_9.1" ssh-rsa AAAAB3NzaC1yc2EAAAAEM1PJxQAAAIEArrHkEG2OvgLKAYZTjzSmXoQs+WV30zdZJuNVI8wZBSjC5q0Hwd797lC9gqqiDQRvyKzDkOj5hOFOYl6mR6GTeR/T2XK+Of0CiMv/Bp8tHXMUdL1W0Mkb59lr3rjG64ZBj3z+TwV3LFINiF0jO6tAXg/zTnqObXJQiaT6igeW1SU= [email]Jupiter@Jupiter.loca[/email]l
'
debug2: key_type_from_name: unknown key type 'environment="SSH_DOUG=RSA_MacOS_10.3.9"'
debug3: key_read: missing keytype
debug2: user_key_allowed: check options: 'environment="SSH_DOUG=RSA_MacOS_10.3.9" ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAIEAzYNvfb4ovqFj5Qxh23VjzhQ/wjYcM7FNyLqU7Lmce4NrCrdU6+dg0RsjWqeI9jFwnzXWGNIjiy4IrHAlnreaNGE6esFNOR/Qew38KkdziWdP53QT0rny3YDFxa0OJAgT9ECAX9YFNjqpv9WnfIoLpVJDUWIjhni263xJIvzNowc= [email]doug@Mars.local-or-doug@Earth.loca[/email]l
'
debug1: Adding to environment: SSH_DOUG=RSA_MacOS_10.3.9
debug1: matching key found: file /home/doug/.ssh/authorized_keys, line 5
Found matching RSA key: 15:56:21:9e:7d:10:88:3d:08:d3:62:8f:5d:0e:48:d9
debug1: restore_uid: 0/0
debug2: userauth_pubkey: authenticated 0 pkalg ssh-rsa
Postponed publickey for doug from 192.168.1.11 port 50032 ssh2
debug1: userauth-request for user doug service ssh-connection method publickey
debug1: attempt 2 failures 1
debug2: input_userauth_request: try method publickey
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-1024
debug1: temporarily_use_uid: 1001/1003 (e=0/0)
debug1: trying public key file /home/doug/.ssh/authorized_keys
debug3: secure_filename: checking '/home/doug/.ssh'
debug3: secure_filename: checking '/home/doug'
debug3: secure_filename: terminating check at '/home/doug'
debug2: key_type_from_name: unknown key type 'environment="SSH_DOUG=RSA_MacOS_9.1"'
debug3: key_read: missing keytype
debug2: user_key_allowed: check options: 'environment="SSH_DOUG=RSA_MacOS_9.1" ssh-rsa AAAAB3NzaC1yc2EAAAAEM1PJxQAAAIEArrHkEG2OvgLKAYZTjzSmXoQs+WV30zdZJuNVI8wZBSjC5q0Hwd797lC9gqqiDQRvyKzDkOj5hOFOYl6mR6GTeR/T2XK+Of0CiMv/Bp8tHXMUdL1W0Mkb59lr3rjG64ZBj3z+TwV3LFINiF0jO6tAXg/zTnqObXJQiaT6igeW1SU= [email]Jupiter@Jupiter.loca[/email]l
'
debug2: key_type_from_name: unknown key type 'environment="SSH_DOUG=RSA_MacOS_10.3.9"'
debug3: key_read: missing keytype
debug2: user_key_allowed: check options: 'environment="SSH_DOUG=RSA_MacOS_10.3.9" ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAIEAzYNvfb4ovqFj5Qxh23VjzhQ/wjYcM7FNyLqU7Lmce4NrCrdU6+dg0RsjWqeI9jFwnzXWGNIjiy4IrHAlnreaNGE6esFNOR/Qew38KkdziWdP53QT0rny3YDFxa0OJAgT9ECAX9YFNjqpv9WnfIoLpVJDUWIjhni263xJIvzNowc= [email]doug@Mars.local-or-doug@Earth.loca[/email]l
'
debug1: Adding to environment: SSH_DOUG=RSA_MacOS_10.3.9
debug1: matching key found: file /home/doug/.ssh/authorized_keys, line 5
Found matching RSA key: 15:56:21:9e:7d:10:88:3d:08:d3:62:8f:5d:0e:48:d9
debug1: restore_uid: 0/0
debug1: ssh_rsa_verify: signature correct
debug2: userauth_pubkey: authenticated 1 pkalg ssh-rsa
debug1: do_pam_account: called
debug3: PAM: do_pam_account pam_acct_mgmt = 0 (Success)
Accepted publickey for doug from 192.168.1.11 port 50032 ssh2
debug1: Entering interactive session for SSH2.
debug2: fd 4 setting O_NONBLOCK
debug2: fd 5 setting O_NONBLOCK
debug1: server_init_dispatch_20
debug1: server_input_channel_open: ctype session rchan 0 win 131072 max 32768
debug1: input_session_request
debug1: channel 0: new [server-session]
debug1: session_new: init
debug1: session_new: session 0
debug1: session_open: channel 0
debug1: session_open: session 0: link with channel 0
debug1: server_input_channel_open: confirm session
debug1: server_input_channel_req: channel 0 request exec reply 0
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req exec
debug1: PAM: establishing credentials
debug2: fd 3 setting TCP_NODELAY
debug2: fd 7 setting O_NONBLOCK
debug3: fd 7 is O_NONBLOCK
debug2: fd 9 setting O_NONBLOCK
debug2: channel 0: read 166 from efd 9
debug2: channel 0: rwin 131072 elen 166 euse 1
debug2: channel 0: sent ext data 166
debug2: channel 0: read 146 from efd 9
debug2: channel 0: rwin 130906 elen 146 euse 1
debug2: channel 0: sent ext data 146
debug2: channel 0: read 243 from efd 9
debug2: channel 0: rwin 130760 elen 243 euse 1
debug2: channel 0: sent ext data 243
debug2: channel 0: read 578 from efd 9
debug2: channel 0: rwin 130517 elen 578 euse 1
debug2: channel 0: sent ext data 578
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug2: notify_done: reading
debug1: Received SIGCHLD.
debug1: session_by_pid: pid 11032
debug1: session_exit_message: session 0 channel 0 pid 11032
debug2: channel 0: request exit-status confirm 0
debug1: session_exit_message: release channel 0
debug2: channel 0: read<=0 rfd 7 len 0
debug2: channel 0: read failed     <-------------   Here is the problem
debug2: channel 0: close_read
debug2: channel 0: input open -> drain
debug2: channel 0: read 0 from efd 9
debug2: channel 0: closing read-efd 9
debug2: channel 0: ibuf empty
debug2: channel 0: send eof
debug2: channel 0: input drain -> closed
debug2: channel 0: send close
debug3: channel 0: will not send data after close
debug2: channel 0: rcvd close
debug3: channel 0: will not send data after close
debug2: channel 0: is dead
debug2: channel 0: gc: notify user
debug1: session_by_channel: session 0 channel 0
debug1: session_close_by_channel: channel 0 child 0
debug1: session_close: session 0 pid 0
debug2: channel 0: gc: user detached
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: server-session, nchannels 1
debug3: channel 0: status: The following connections are open:
  #0 server-session (t4 r0 i3/0 o3/0 fd 7/7 cfd -1)

debug3: channel 0: close_fds r 7 w 7 e -1 c -1
Connection closed by 192.168.1.11
debug1: do_cleanup
debug1: PAM: cleanup
debug3: PAM: sshpam_thread_cleanup entering
Closing connection to 192.168.1.11
debug1: PAM: cleanup

---

### Post by DougMcNutt on 2008-09-22
Some more info that might be germane:

I am a csh bigot and have been that way for more than 30 years. I'm too old to change that.

SSH, The secure Shell by Barrett and Silverman, O'Reilly 2001 is a bit out of date but it's the best I can find.

Page 191 says that SSH2 disables reading of $HOME.cshrc and .tcshrc for subsystems like sftp_server which handles both scp and sftp.  That is NOT happening. My .tcshrc and /etc/csh.cshrc are both getting executed - er sourced. The book warns that csh thingies like that can affect scp if they write to standard out which mine do.

The line "AllowCshrcSourcingWithSubsystems no" in the config for sshd is not accepted by the version on Ubuntu Hardy Heron.

Are my scp efforts failing because of tcsh? I put a test for $?SSH_CLIENT at the start of the two sourced rc files and jumped with a goto to skip the rest of the file. They're working and no real actions are now performed on an ssh connection of any kind even though I still want them on a simple ssh login.

scp still doesn't work failing with a read failure on the machine on which the target file resides.

Has sshd been tested at all with csh or tcsh?

Where can I find documentation like O'Reilly for the actual ssh package installed with Hardy Heron? is it OpenSSH or BSD SSH2?

---

### Post by DougMcNutt on 2008-09-24
scp now works, at least for me.

The first problem I noticed was immediately after a ubuntu upgrade sometime near April 2008. An obvious change to the ssh package was inclusion of a blacklist that suppressed dangerous certificates that were produced by non-prime factors in ssh-keygen on Debian systems. I had an investment in certificates produced under MacOSXand possibly cygwin that I didn't want to change and I blamed the blacklist for failure of scp. That was wrong but it caused me to make unwise changes to sshd_config that very likely obscured the real problem.

At one point ssh complained about SELinux and the lack of support for some Kerberos realms and other stuff I still don't know about. Last week we attempted to re-install an older version of openssh and experienced a total failure that resulted in a reload of the current ubuntu version without SELinux.

I discovered, reading "SSH, the Secure Shell" from O'Reilly (2001, ISBN 0-596-00011-1, pdf now on the O'Reilly site) that scp could be messed up by actions in shell startup files that write to standard out. The same book also says that, at least for the cshell which is my preference, the ssh daemon calls tcsh with the -f (fast) option that suppresses processing of the startup files altogether.

I have learned that sshd does source ~/.tcshrc and /etc/csh.chsrc regardless. It's possible that the code was changed along with the release in April. It's also possible that the book was wrong in the first place. But then scp did work OK until the April update.

The book also warns that use of an ssh_agent preloaded with certificates causes any -i option, to specify a particular certificate, to be ignored. I was fooled when I tried to test for blacklisting by making ssh calls with a -i. The scp tool went its merry way with the certs in the order stored in the agent even when I added the ubuntu cert to the agent.

The status now is that scp is working fine with my changes to ~/.tcsh and /etc/csh.chsrc. I have no idea what corresponding changes to ~/.bashrc and other goodies like ~/.profile might be required. Just don't use any echos or cats.

I am enclosing my /etc/ssh/sshd_config and ~/.tcshrc files which I commented as I went along.  Enjoy. I consider the case closed.

sshd_config

```

# Package generated configuration file
# Modified by Doug McNutt, www.macnauchtan.com
# See the sshd(8) manpage for details
# Ubuntu's man file is not complete. Try this, which may not include Debian goodies:
# http://www.openbsd.org/cgi-bin/man.cgi?query=sshd_config&sektion=5
# Some ideas for this file come from
# http://tintax.net/2008/05/31/secure-shell-and-public-key-cryptography/

# What ports, IPs and protocols we listen for
Port 22

# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0

# Don't support protocol 1. Even ssh for OS 9 seems to be OK with version 2.
Protocol 2

# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
# AuthorizedKeysFile    %h/.ssh/authorized_keys

# This allows for environment options in the authorizedKeys files
PermitUserEnvironment yes

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Yes implies that you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
IgnoreUserKnownHosts no

# Disable black listed key usage (update your keys!)
# We once turned blacklisting off but it appears that was not the problem with scp
# There are several keys in use that were generated in MacOS and I really think they're OK.
PermitBlacklistedKeys no

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Handle incoming traffic as an unprivileged user until user is verified.
UsePrivilegeSeparation yes

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads) Refer to login.conf(5)
ChallengeResponseAuthentication no

# DPM Change this to no after it all works. For now there are too many other machines to fix up.
PasswordAuthentication yes

# Kerberos options
# Around here there is no Kerberos.
KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# Generic Security Services Application Program Interface in the acronym
# But I still don'tknow what it's all about.
# GSSAPI options
GSSAPIAuthentication no
GSSAPICleanupCredentials no
GSSAPIKeyExchange no
GSSAPIKeyExchange no

# Allow connections that need a GUI interface using X11 over the network
X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

# The Pluggable Authentication Module, PAM, for checking accounts (including
# password validity if using password authentication)instead of ssh server itself
# May conflict with ordinary ssh password authentication. A ubuntu or Debian thing, I think.
UsePAM no

# Accept the default simultaneous connection limits
#MaxStartups 10:30:60

# Don't provide a banner. Damned lawyers anyway.
#Banner /etc/issue.net

# Allow client to pass locale environment variables
# Note the trailing e in locale. We DO permit local environment variables.
# AcceptEnv LANG LC_*
AcceptEnv yes

Subsystem sftp /usr/lib/openssh/sftp-server
# From O'Reilly SSH book page 191. ISBN 0-596-00011-1
# My .tcshrc IS getting called by scp even though O'Reilly says no.
# sshd will not accept the command commented out below.
# AllowCshrcSourcingWithSubsystems no

```

~/.tcshrc

```
setenv LOGS $HOME/logs
if ($?SHELLOG) then
       set thelog = $SHELLOG
else if ($?REMOTEHOST) then
    set thelog = $LOGS/shell_$REMOTEHOST
else
    set thelog = $LOGS/shell
endif
setenv SHELLOG $thelog
echo " "   >> $thelog
date  >> $thelog
echo "SHLVL is $SHLVL"  >> $thelog
echo "PATH on entry is $PATH"  >> $thelog
# Enable this line to see the whole environment at entry time.
# setenv >> $SHELLOG

# Add ~/bin to the beginning of the PATH but don't do it if it's already there.
if ($path[1] != /home/doug/bin) then
    setenv PATH $HOME/bin:$PATH
endif

# Log a few items for debugging
echo Command line arguments: $0 $*  >> $thelog
# SSH_DOUG gets set by entries in the SSH authorized_keys file.
if ($?SSH_DOUG) then
    echo \$SSH_DOUG is $SSH_DOUG  >> $thelog
endif
if ($?DISPLAY) then
    echo \$DISPLAY is $DISPLAY  >> $thelog
endif
if ($?TERM) then
    echo \$TERM is $TERM  >> $thelog
endif
if ($?REMOTEHOST) then
    echo \$REMOTEHOST is $REMOTEHOST  >> $thelog
endif
if ($?prompt) then
    echo \$prompt is $prompt  >> $thelog
endif
if ($?loginsh) then
    echo "Entered as a login shell"  >> $thelog
endif
#
# Set up Doug's favorite command aliases
alias la ls -aF
set prompt = "$HOST[%c3]%# "
#
# See if we're logging in from elsewhere. If not and we're logging in, start some things up.
# But don't attempt to start applications that are already running.
# Also check for use by an SSH scp or sftp request.
# Use a goto to skip any writing to standard out. This file is sourced - don't "exit".
# Note that a similar change is required in /etc/csh.cshrc.
# Test REMOTEHOST first so we can set the prompt to point to us. Just to keep users informed.
if ($?REMOTEHOST) then
    echo "Hello $REMOTEHOST, welcome to $HOST."
    set prompt = "$HOST[%c3]%# "
else if ($?SSH_CLIENT) then
    goto EARLYOUT
else if ($SHLVL == 1) then
    echo "Starting applications if appropriate"  >> $thelog
    if (! `pgrep -c -u $USER gedit`) then
        gedit $HOME/ScratchPad >>& $LOGS/gedit &
    endif
    if (! `pgrep -c -u $USER claws-mail`) then
        claws-mail >>& $LOGS/claws &
    endif
    echo Welcome to $HOST
endif

EARLYOUT:

```

---

### Post by threeta on 2012-02-23
scp sends full size packets (1500) and then some extra for encryption.  your firewall probably stops the larger than 1550 packets and thus your scp.

Set the mtu size down slightly.  The packet comes in at 1500, gets encryption on top, and then the firewall will drop....

add mtu 1300 to the end of the hostname in /etc/hostname.interface:
akcux63 mtu 1300

restart networking

---

### Post by cariboo on 2012-02-24
This thread is 4 years old, let's put it back to sleep.

---


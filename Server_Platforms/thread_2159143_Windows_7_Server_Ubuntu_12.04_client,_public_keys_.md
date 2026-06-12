---
title: "Windows 7 Server Ubuntu 12.04 client, public keys being refused, please help."
date: 2013-07-02
forum: Server Platforms
---

### Post by lilmudd on 2013-07-02
Scenario, needed to log into a windows7 server running fresshd and Wincp. Need to be able to transfer files from the Ubuntu machine ( client) to the server ( windows 7) and take from server and put on the client.

Am utilizing sftp as i am able to move the files while i have password authentication enabled, however i need to turn it off and have pub key and priv keys work.

I have made them on puttygen done all the converting etc to make them the right files for openssh, however i am using freesshd i am pretty sure they use the same framework though not sure.

Either way i need to be able to use what I have currently installed. The id_dsa files are holding the public and private keys made from the puttygen on windows side. For freesshd I have moved the public key that goes with the private one into a folder on the desktop and directed it to look there for the file.

EDIT: was on nat instead of host-only when testing, do not think it matters because I still can not log in with keys but password words

any and all help would be great!!

[EMAIL="alex3@alex3-VirtualBox:~/.ssh"]alex3@alex3-VirtualBox:~/.ssh[/EMAIL]$ sftp -vvvvvv alex@192.168.56.102 
OpenSSH_5.9p1 Debian-5ubuntu1.1, OpenSSL 1.0.1 14 Mar 2012 
debug1: Reading configuration data /etc/ssh/ssh_config 
debug1: /etc/ssh/ssh_config line 19: Applying options for * 
debug2: ssh_connect: needpriv 0 
debug1: Connecting to 192.168.56.102 [192.168.56.102] port 22. 
debug1: Connection established. 
debug1: identity file /home/alex3/.ssh/id_rsa type -1 
debug1: identity file /home/alex3/.ssh/id_rsa-cert type -1 
debug3: Incorrect RSA1 identifier 
debug3: Could not load "/home/alex3/.ssh/id_dsa" as a RSA1 public key 
debug1: identity file /home/alex3/.ssh/id_dsa type 1 
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-1024 
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-1024 
debug1: identity file /home/alex3/.ssh/id_dsa-cert type -1 
debug1: identity file /home/alex3/.ssh/id_ecdsa type -1 
debug1: identity file /home/alex3/.ssh/id_ecdsa-cert type -1 
debug1: Remote protocol version 2.0, remote software version WeOnlyDo 2.1.3 
debug1: no match: WeOnlyDo 2.1.3 
debug1: Enabling compatibility mode for protocol 2.0 
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.1 
debug2: fd 3 setting O_NONBLOCK 
debug3: load_hostkeys: loading entries for host "192.168.56.102" from file "/home/alex3/.ssh/known_hosts" 
debug3: load_hostkeys: found key type RSA in file /home/alex3/.ssh/known_hosts:1 
debug3: load_hostkeys: loaded 1 keys 
debug3: order_hostkeyalgs: prefer hostkeyalgs: [email]ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com[/email],ssh-rsa 
debug1: SSH2_MSG_KEXINIT sent 
debug1: SSH2_MSG_KEXINIT received 
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1 
debug2: kex_parse_kexinit: [email]ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa,ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com[/email],ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-dss 
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se 
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se 
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96 
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96 
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib 
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group1-sha1,diffie-hellman-group14-sha1 
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss 
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,aes192-cbc,aes256-cbc,rijndael128-cbc,rijndael192-cbc,rijndael256-cbc,rijndael-cbc@lysator.liu.se 
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,aes192-cbc,aes256-cbc,rijndael128-cbc,rijndael192-cbc,rijndael256-cbc,rijndael-cbc@lysator.liu.se 
debug2: kex_parse_kexinit: hmac-sha1,hmac-sha1-96,hmac-md5,none 
debug2: kex_parse_kexinit: hmac-sha1,hmac-sha1-96,hmac-md5,none 
debug2: kex_parse_kexinit: zlib,none 
debug2: kex_parse_kexinit: zlib,none 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5 
debug1: kex: server->client aes128-cbc hmac-md5 none 
debug2: mac_setup: found hmac-md5 
debug1: kex: client->server aes128-cbc hmac-md5 none 
debug2: dh_gen_key: priv key bits set: 134/256 
debug2: bits set: 990/2048 
debug1: sending SSH2_MSG_KEXDH_INIT 
debug1: expecting SSH2_MSG_KEXDH_REPLY 
debug1: Server host key: RSA 55:df:d7:e1:db:86:d3:6e:6f:d5:0f:89:06:4a:e4:f5 
debug3: load_hostkeys: loading entries for host "192.168.56.102" from file "/home/alex3/.ssh/known_hosts" 
debug3: load_hostkeys: found key type RSA in file /home/alex3/.ssh/known_hosts:1 
debug3: load_hostkeys: loaded 1 keys 
debug1: Host '192.168.56.102' is known and matches the RSA host key. 
debug1: Found key in /home/alex3/.ssh/known_hosts:1 
debug2: bits set: 1035/2048 
debug1: ssh_rsa_verify: signature correct 
debug2: kex_derive_keys 
debug2: set_newkeys: mode 1 
debug1: SSH2_MSG_NEWKEYS sent 
debug1: expecting SSH2_MSG_NEWKEYS 
debug2: set_newkeys: mode 0 
debug1: SSH2_MSG_NEWKEYS received 
debug1: Roaming not allowed by server 
debug1: SSH2_MSG_SERVICE_REQUEST sent 
debug2: service_accept: ssh-userauth 
debug1: SSH2_MSG_SERVICE_ACCEPT received 
debug2: key: /home/alex3/.ssh/id_dsa (0x7f941ed81490) 
debug2: key: /home/alex3/.ssh/id_rsa ((nil)) 
debug2: key: /home/alex3/.ssh/id_ecdsa ((nil)) 
debug1: Authentications that can continue: publickey 
debug3: start over, passed a different list publickey 
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password 
debug3: authmethod_lookup publickey 
debug3: remaining preferred: keyboard-interactive,password 
debug3: authmethod_is_enabled publickey 
debug1: Next authentication method: publickey 
debug1: Offering RSA public key: /home/alex3/.ssh/id_dsa 
debug3: send_pubkey_test 
debug2: we sent a publickey packet, wait for reply 
debug1: Server accepts key: pkalg ssh-rsa blen 149 
debug2: input_userauth_pk_ok: fp 49:9a:50:58:60:61:6c:d0:de:b6:98:60:1f:cc:0d:a5 
debug3: sign_and_send_pubkey: RSA 49:9a:50:58:60:61:6c:d0:de:b6:98:60:1f:cc:0d:a5 
debug1: Authentications that can continue: publickey 
debug1: Trying private key: /home/alex3/.ssh/id_rsa 
debug3: no such identity: /home/alex3/.ssh/id_rsa 
debug1: Trying private key: /home/alex3/.ssh/id_ecdsa 
debug3: no such identity: /home/alex3/.ssh/id_ecdsa 
debug2: we did not send a packet, disable method 
debug1: No more authentication methods to try. 
Permission denied (publickey). 
Couldn't read packet: Connection reset by peer 
[EMAIL="alex3@alex3-VirtualBox:~/.ssh"]alex3@alex3-VirtualBox:~/.ssh[/EMAIL]$ sftp -vvvvvv alex@192.168.56.102 
OpenSSH_5.9p1 Debian-5ubuntu1.1, OpenSSL 1.0.1 14 Mar 2012 
debug1: Reading configuration data /etc/ssh/ssh_config 
debug1: /etc/ssh/ssh_config line 19: Applying options for * 
debug2: ssh_connect: needpriv 0 
debug1: Connecting to 192.168.56.102 [192.168.56.102] port 22. 
debug1: Connection established. 
debug1: identity file /home/alex3/.ssh/id_rsa type -1 
debug1: identity file /home/alex3/.ssh/id_rsa-cert type -1 
debug3: Incorrect RSA1 identifier 
debug3: Could not load "/home/alex3/.ssh/id_dsa" as a RSA1 public key 
debug1: identity file /home/alex3/.ssh/id_dsa type 1 
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-1024 
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-1024 
debug1: identity file /home/alex3/.ssh/id_dsa-cert type -1 
debug1: identity file /home/alex3/.ssh/id_ecdsa type -1 
debug1: identity file /home/alex3/.ssh/id_ecdsa-cert type -1 
debug1: Remote protocol version 2.0, remote software version WeOnlyDo 2.1.3 
debug1: no match: WeOnlyDo 2.1.3 
debug1: Enabling compatibility mode for protocol 2.0 
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.1 
debug2: fd 3 setting O_NONBLOCK 
debug3: load_hostkeys: loading entries for host "192.168.56.102" from file "/home/alex3/.ssh/known_hosts" 
debug3: load_hostkeys: found key type RSA in file /home/alex3/.ssh/known_hosts:1 
debug3: load_hostkeys: loaded 1 keys 
debug3: order_hostkeyalgs: prefer hostkeyalgs: [email]ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com[/email],ssh-rsa 
debug1: SSH2_MSG_KEXINIT sent 
debug1: SSH2_MSG_KEXINIT received 
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1 
debug2: kex_parse_kexinit: [email]ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa,ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com[/email],ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-dss 
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se 
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se 
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96 
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96 
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib 
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group1-sha1,diffie-hellman-group14-sha1 
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss 
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,aes192-cbc,aes256-cbc,rijndael128-cbc,rijndael192-cbc,rijndael256-cbc,rijndael-cbc@lysator.liu.se 
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,aes192-cbc,aes256-cbc,rijndael128-cbc,rijndael192-cbc,rijndael256-cbc,rijndael-cbc@lysator.liu.se 
debug2: kex_parse_kexinit: hmac-sha1,hmac-sha1-96,hmac-md5,none 
debug2: kex_parse_kexinit: hmac-sha1,hmac-sha1-96,hmac-md5,none 
debug2: kex_parse_kexinit: zlib,none 
debug2: kex_parse_kexinit: zlib,none 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5 
debug1: kex: server->client aes128-cbc hmac-md5 none 
debug2: mac_setup: found hmac-md5 
debug1: kex: client->server aes128-cbc hmac-md5 none 
debug2: dh_gen_key: priv key bits set: 128/256 
debug2: bits set: 1038/2048 
debug1: sending SSH2_MSG_KEXDH_INIT 
debug1: expecting SSH2_MSG_KEXDH_REPLY 
debug1: Server host key: RSA 55:df:d7:e1:db:86:d3:6e:6f:d5:0f:89:06:4a:e4:f5 
debug3: load_hostkeys: loading entries for host "192.168.56.102" from file "/home/alex3/.ssh/known_hosts" 
debug3: load_hostkeys: found key type RSA in file /home/alex3/.ssh/known_hosts:1 
debug3: load_hostkeys: loaded 1 keys 
debug1: Host '192.168.56.102' is known and matches the RSA host key. 
debug1: Found key in /home/alex3/.ssh/known_hosts:1 
debug2: bits set: 1064/2048 
debug1: ssh_rsa_verify: signature correct 
debug2: kex_derive_keys 
debug2: set_newkeys: mode 1 
debug1: SSH2_MSG_NEWKEYS sent 
debug1: expecting SSH2_MSG_NEWKEYS 
debug2: set_newkeys: mode 0 
debug1: SSH2_MSG_NEWKEYS received 
debug1: Roaming not allowed by server 
debug1: SSH2_MSG_SERVICE_REQUEST sent 
debug2: service_accept: ssh-userauth 
debug1: SSH2_MSG_SERVICE_ACCEPT received 
debug2: key: /home/alex3/.ssh/id_dsa (0x7f11cfb6f490) 
debug2: key: /home/alex3/.ssh/id_rsa ((nil)) 
debug2: key: /home/alex3/.ssh/id_ecdsa ((nil)) 
debug1: Authentications that can continue: password,publickey 
debug3: start over, passed a different list password,publickey 
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password 
debug3: authmethod_lookup publickey 
debug3: remaining preferred: keyboard-interactive,password 
debug3: authmethod_is_enabled publickey 
debug1: Next authentication method: publickey 
debug1: Offering RSA public key: /home/alex3/.ssh/id_dsa 
debug3: send_pubkey_test 
debug2: we sent a publickey packet, wait for reply 
debug1: Server accepts key: pkalg ssh-rsa blen 149 
debug2: input_userauth_pk_ok: fp 49:9a:50:58:60:61:6c:d0:de:b6:98:60:1f:cc:0d:a5 
debug3: sign_and_send_pubkey: RSA 49:9a:50:58:60:61:6c:d0:de:b6:98:60:1f:cc:0d:a5 
debug1: Authentications that can continue: password,publickey 
debug1: Trying private key: /home/alex3/.ssh/id_rsa 
debug3: no such identity: /home/alex3/.ssh/id_rsa 
debug1: Trying private key: /home/alex3/.ssh/id_ecdsa 
debug3: no such identity: /home/alex3/.ssh/id_ecdsa 
debug2: we did not send a packet, disable method 
debug3: authmethod_lookup password 
debug3: remaining preferred: ,password 
debug3: authmethod_is_enabled password 
debug1: Next authentication method: password 
alex@192.168.56.102's password: 
debug3: packet_send2: adding 64 (len 57 padlen 7 extra_pad 64) 
debug2: we sent a password packet, wait for reply 
debug1: Authentication succeeded (password). 
Authenticated to 192.168.56.102 ([192.168.56.102]:22). 
debug2: fd 4 setting O_NONBLOCK 
debug3: fd 5 is O_NONBLOCK 
debug1: channel 0: new [client-session] 
debug3: ssh_session2_open: channel_new: 0 
debug2: channel 0: send open 
debug1: Entering interactive session. 
debug2: callback start 
debug2: client_session2_setup: id 0 
debug2: fd 3 setting TCP_NODELAY 
debug1: Sending environment. 
debug3: Ignored env SSH_AGENT_PID 
debug3: Ignored env GPG_AGENT_INFO 
debug3: Ignored env TERM 
debug3: Ignored env SHELL 
debug3: Ignored env XDG_SESSION_COOKIE 
debug3: Ignored env WINDOWID 
debug3: Ignored env GNOME_KEYRING_CONTROL 
debug3: Ignored env USER 
debug3: Ignored env LS_COLORS 
debug3: Ignored env XDG_SESSION_PATH 
debug3: Ignored env XDG_SEAT_PATH 
debug3: Ignored env SSH_AUTH_SOCK 
debug3: Ignored env SESSION_MANAGER 
debug3: Ignored env DEFAULTS_PATH 
debug3: Ignored env XDG_CONFIG_DIRS 
debug3: Ignored env PATH 
debug3: Ignored env DESKTOP_SESSION 
debug3: Ignored env PWD 
debug3: Ignored env GNOME_KEYRING_PID 
debug1: Sending env LANG = en_US.UTF-8 
debug2: channel 0: request env confirm 0 
debug3: Ignored env MANDATORY_PATH 
debug3: Ignored env UBUNTU_MENUPROXY 
debug3: Ignored env GDMSESSION 
debug3: Ignored env SHLVL 
debug3: Ignored env HOME 
debug3: Ignored env GNOME_DESKTOP_SESSION_ID 
debug3: Ignored env LOGNAME 
debug3: Ignored env XDG_DATA_DIRS 
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS 
debug3: Ignored env LESSOPEN 
debug3: Ignored env DISPLAY 
debug3: Ignored env XDG_CURRENT_DESKTOP 
debug3: Ignored env LESSCLOSE 
debug3: Ignored env COLORTERM 
debug3: Ignored env XAUTHORITY 
debug3: Ignored env _ 
debug3: Ignored env OLDPWD 
debug1: Sending subsystem: sftp 
debug2: channel 0: request subsystem confirm 1 
debug2: callback done 
debug2: channel 0: open confirm rwindow 131072 rmax 98304 
debug2: channel_input_status_confirm: type 99 id 0 
debug2: subsystem request accepted on channel 0 
debug2: channel 0: rcvd adjust 0 
debug2: Remote version: 3 
Connected to 192.168.56.102. 
debug3: Sent message fd 3 T:16 I:32750 
debug3: SSH_FXP_REALPATH . -> / 
sftp> bye 
bye 
debug2: channel 0: read<=0 rfd 4 len 0 
debug2: channel 0: read failed 
debug2: channel 0: close_read 
debug2: channel 0: input open -> drain 
debug2: channel 0: ibuf empty 
debug2: channel 0: send eof 
debug2: channel 0: input drain -> closed 
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0 
debug2: channel 0: rcvd close 
debug2: channel 0: output open -> drain 
debug3: channel 0: will not send data after close 
debug2: channel 0: obuf empty 
debug2: channel 0: close_write 
debug2: channel 0: output drain -> closed 
debug2: channel 0: almost dead 
debug2: channel 0: gc: notify user 
debug2: channel 0: gc: user detached 
debug2: channel 0: send close 
debug2: channel 0: is dead 
debug2: channel 0: garbage collecting 
debug1: channel 0: free: client-session, nchannels 1 
debug3: channel 0: status: The following connections are open: 
  #0 client-session (t4 r0 i3/0 o3/0 fd -1/-1 cc -1) 

debug1: fd 0 clearing O_NONBLOCK 
debug3: fd 1 is not O_NONBLOCK 
Transferred: sent 2648, received 1632 bytes, in 4.6 seconds 
Bytes per second: sent 578.1, received 356.3 
debug1: Exit status 0 
[EMAIL="alex3@alex3-VirtualBox:~/.ssh"]alex3@alex3-VirtualBox:~/.ssh[/EMAIL]$ sftp -vvv alex@192.168.56.102 
OpenSSH_5.9p1 Debian-5ubuntu1.1, OpenSSL 1.0.1 14 Mar 2012 
debug1: Reading configuration data /etc/ssh/ssh_config 
debug1: /etc/ssh/ssh_config line 19: Applying options for * 
debug2: ssh_connect: needpriv 0 
debug1: Connecting to 192.168.56.102 [192.168.56.102] port 22. 
debug1: Connection established. 
debug1: identity file /home/alex3/.ssh/id_rsa type -1 
debug1: identity file /home/alex3/.ssh/id_rsa-cert type -1 
debug3: Incorrect RSA1 identifier 
debug3: Could not load "/home/alex3/.ssh/id_dsa" as a RSA1 public key 
debug1: identity file /home/alex3/.ssh/id_dsa type 1 
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-1024 
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-1024 
debug1: identity file /home/alex3/.ssh/id_dsa-cert type -1 
debug1: identity file /home/alex3/.ssh/id_ecdsa type -1 
debug1: identity file /home/alex3/.ssh/id_ecdsa-cert type -1 
debug1: Remote protocol version 2.0, remote software version WeOnlyDo 2.1.3 
debug1: no match: WeOnlyDo 2.1.3 
debug1: Enabling compatibility mode for protocol 2.0 
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.1 
debug2: fd 3 setting O_NONBLOCK 
debug3: load_hostkeys: loading entries for host "192.168.56.102" from file "/home/alex3/.ssh/known_hosts" 
debug3: load_hostkeys: found key type RSA in file /home/alex3/.ssh/known_hosts:1 
debug3: load_hostkeys: loaded 1 keys 
debug3: order_hostkeyalgs: prefer hostkeyalgs: [email]ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com[/email],ssh-rsa 
debug1: SSH2_MSG_KEXINIT sent 
debug1: SSH2_MSG_KEXINIT received 
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1 
debug2: kex_parse_kexinit: [email]ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa,ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com[/email],ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-dss 
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se 
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se 
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96 
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96 
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib 
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group1-sha1,diffie-hellman-group14-sha1 
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss 
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,aes192-cbc,aes256-cbc,rijndael128-cbc,rijndael192-cbc,rijndael256-cbc,rijndael-cbc@lysator.liu.se 
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,aes192-cbc,aes256-cbc,rijndael128-cbc,rijndael192-cbc,rijndael256-cbc,rijndael-cbc@lysator.liu.se 
debug2: kex_parse_kexinit: hmac-sha1,hmac-sha1-96,hmac-md5,none 
debug2: kex_parse_kexinit: hmac-sha1,hmac-sha1-96,hmac-md5,none 
debug2: kex_parse_kexinit: zlib,none 
debug2: kex_parse_kexinit: zlib,none 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5 
debug1: kex: server->client aes128-cbc hmac-md5 none 
debug2: mac_setup: found hmac-md5 
debug1: kex: client->server aes128-cbc hmac-md5 none 
debug2: dh_gen_key: priv key bits set: 117/256 
debug2: bits set: 1023/2048 
debug1: sending SSH2_MSG_KEXDH_INIT 
debug1: expecting SSH2_MSG_KEXDH_REPLY 
debug1: Server host key: RSA 55:df:d7:e1:db:86:d3:6e:6f:d5:0f:89:06:4a:e4:f5 
debug3: load_hostkeys: loading entries for host "192.168.56.102" from file "/home/alex3/.ssh/known_hosts" 
debug3: load_hostkeys: found key type RSA in file /home/alex3/.ssh/known_hosts:1 
debug3: load_hostkeys: loaded 1 keys 
debug1: Host '192.168.56.102' is known and matches the RSA host key. 
debug1: Found key in /home/alex3/.ssh/known_hosts:1 
debug2: bits set: 1002/2048 
debug1: ssh_rsa_verify: signature correct 
debug2: kex_derive_keys 
debug2: set_newkeys: mode 1 
debug1: SSH2_MSG_NEWKEYS sent 
debug1: expecting SSH2_MSG_NEWKEYS 
debug2: set_newkeys: mode 0 
debug1: SSH2_MSG_NEWKEYS received 
debug1: Roaming not allowed by server 
debug1: SSH2_MSG_SERVICE_REQUEST sent 
debug2: service_accept: ssh-userauth 
debug1: SSH2_MSG_SERVICE_ACCEPT received 
debug2: key: /home/alex3/.ssh/id_dsa (0x7f2ac9fca490) 
debug2: key: /home/alex3/.ssh/id_rsa ((nil)) 
debug2: key: /home/alex3/.ssh/id_ecdsa ((nil)) 
debug1: Authentications that can continue: password,publickey 
debug3: start over, passed a different list password,publickey 
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password 
debug3: authmethod_lookup publickey 
debug3: remaining preferred: keyboard-interactive,password 
debug3: authmethod_is_enabled publickey 
debug1: Next authentication method: publickey 
debug1: Offering RSA public key: /home/alex3/.ssh/id_dsa 
debug3: send_pubkey_test 
debug2: we sent a publickey packet, wait for reply 
debug1: Server accepts key: pkalg ssh-rsa blen 149 
debug2: input_userauth_pk_ok: fp 49:9a:50:58:60:61:6c:d0:de:b6:98:60:1f:cc:0d:a5 
debug3: sign_and_send_pubkey: RSA 49:9a:50:58:60:61:6c:d0:de:b6:98:60:1f:cc:0d:a5 
debug1: Authentications that can continue: password,publickey 
debug1: Trying private key: /home/alex3/.ssh/id_rsa 
debug3: no such identity: /home/alex3/.ssh/id_rsa 
debug1: Trying private key: /home/alex3/.ssh/id_ecdsa 
debug3: no such identity: /home/alex3/.ssh/id_ecdsa 
debug2: we did not send a packet, disable method 
debug3: authmethod_lookup password 
debug3: remaining preferred: ,password 
debug3: authmethod_is_enabled password 
debug1: Next authentication method: password 
alex@192.168.56.102's password:

---


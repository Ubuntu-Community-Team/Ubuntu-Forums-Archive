---
title: "Denyhosts/sshd compatibility issue (?)"
date: 2009-10-07
forum: Security
---

### Post by Jive Turkey on 2009-10-07
On the website for the denyhosts project at: [http://denyhosts.sourceforge.net/ssh_config.html]("http://denyhosts.sourceforge.net/ssh_config.html")

[HTML]Testing you SSH configuration
In order to take advantage of DenyHosts, you must ensure that your sshd server has been compiled w/ tcp_wrappers support. On most Linux distros, sshd has been compiled with tcp_wrappers enabled. If you are not sure, a simple test follows:

   1. Login, as root, to your Linux system containing the sshd server.
   2. Edit the file, /etc/hosts.deny
   3. Add the following:
      $ sshd: 127.0.0.1
   4. Save the file
   5. Attempt to connect to the local sshd server:
      $ ssh localhost
   6. You should see the following ssh error message:
      ssh_exchange_identification: Connection closed by remote host

      If the above error message was displayed, then sshd has been compiled with tcp_wrappers

      If your client connects to the sshd server, then your sshd has not been compiled with tcp_wrappers

   7. Edit the file, /etc/hosts.deny
   8. Remove the line that you added earlier (eg. sshd: 127.0.0.1)
   9. Save the file [/HTML]

According to this the my sshd server (OpenSSH_5.1p1 Debian-5ubuntu1) will not benefit from using denyhosts.  After some testing I have found that denyhosts from the repositories is not functioning as advertised either. 

How about you all?

---

### Post by Lars Noodén on 2009-10-08
That package depends on tcpd and support for tcpd in openssh-server

Put something like this in tcpd's /etc/hosts.deny for a test:

[INDENT][FONT="Courier New"]
sshd: 127.0.0.0/8
[/FONT][/INDENT]

Stop the ssh server and then re-start it for a one-off session in debug mode:

[indent]
[FONT="Courier New"]/etc/init.d/ssh stop
/usr/sbin/sshd -Dd
[/FONT][/indent]

Then in another window try to connect.   Go back to the sshd window and read the output.  sshd will stop once the connection is closed and you'll have to run it again for each test.  

You should see something like this:
[INDENT][FONT="Courier New"]debug1: Connection refused by tcp wrapper[/FONT][/INDENT]

Note that all of the above is done on the same machine.

PS.  It works for me with OpenSSH_5.1p1 Debian-6ubuntu1, OpenSSL 0.9.8g 19 Oct 2007 on karmic beta on amd64.

---

### Post by CharlesA on 2009-10-08
I've had it lock me out when I screwed up my username (but that was due to me being stupid and not putting my IP in the hosts.allow file..)

---

### Post by Jive Turkey on 2009-10-08
@Lars

Thanks, it worked the way you set it up.  I was concerned that sshd may have been compiled w/o the required option.

---

### Post by Lars Noodén on 2009-10-09
@  Jive Turkey : You're welcome.

> **CharlesA said:**
> I've had it lock me out when I screwed up my username (but that was due to me being stupid and not putting my IP in the hosts.allow file..)

@ CharlesA:

Been there.  Done that.  Here's a trick to avoid that long embarrassing walk to the server room:


Step 1 - preparation:

```

cp /etc/hosts.allow /tmp/hosts.allow.works
cp /etc/hosts.deny  /tmp/hosts.deny.works

```

Step 2 - ten minute deadline to test your changes

```

echo "cp /etc/hosts.allow.works /tmp/hosts.allow; \
     cp /etc/hosts.deny.works /tmp/hosts.deny; " \
     | sudo at now +10 minutes

```

Step 3 - you now have 9 minutes to save your changes and try logging in.

The same kind of emergency eject can be done with iptables (iptables-save + iptables-restore), making changes to sshd_config or anything else that risks locking you out.  If you are messing with sudoers, then don't include sudo in the recipe.

---

### Post by devnulljp on 2009-11-15
> **Lars Noodén said:**
> That package depends on tcpd and support for tcpd in openssh-server

Put something like this in tcpd's /etc/hosts.deny for a test:

[INDENT][FONT="Courier New"]
sshd: 127.0.0.0/8
[/FONT][/INDENT]

Stop the ssh server and then re-start it for a one-off session in debug mode:

[indent]
[FONT="Courier New"]/etc/init.d/ssh stop
/usr/sbin/sshd -Dd
[/FONT][/indent]

Then in another window try to connect.   Go back to the sshd window and read the output.  sshd will stop once the connection is closed and you'll have to run it again for each test.  

You should see something like this:
[INDENT][FONT="Courier New"]debug1: Connection refused by tcp wrapper[/FONT][/INDENT]

Note that all of the above is done on the same machine.

PS.  It works for me with OpenSSH_5.1p1 Debian-6ubuntu1, OpenSSL 0.9.8g 19 Oct 2007 on karmic beta on amd64.I just tried that and it let me in...any suggestions? 

```
debug1: sshd version OpenSSH_5.1p1 Debian-6ubuntu2                                                                                                                                  
debug1: read PEM private key done: type RSA                                                                                                                                         
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048                                                                                                                   
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048                                                                                                                         
debug1: private host key: #0 type 1 RSA                                                                                                                                             
debug1: read PEM private key done: type DSA                                                                                                                                         
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024                                                                                                                   
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024                                                                                                                         
debug1: private host key: #1 type 2 DSA                                                                                                                                             
debug1: rexec_argv[0]='/usr/sbin/sshd'                                                                                                                                              
debug1: rexec_argv[1]='-Dd'                                                                                                                                                         
debug1: Bind to port 22 on 0.0.0.0.                                                                                                                                                 
Server listening on 0.0.0.0 port 22.                                                                                                                                                
debug1: Bind to port 22 on ::.                                                                                                                                                      
Server listening on :: port 22.                                                                                                                                                     
debug1: Server will not fork when running in debugging mode.                                                                                                                        
debug1: rexec start in 5 out 5 newsock 5 pipe -1 sock 8                                                                                                                             
debug1: inetd sockets after dupping: 3, 3                                                                                                                                           
Connection from ::1 port 45195                                                                                                                                                      
debug1: Client protocol version 2.0; client software version OpenSSH_5.1p1 Debian-6ubuntu2                                                                                          
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*                                                                                                                           
debug1: Enabling compatibility mode for protocol 2.0                                                                                                                                
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2                                                                                                                  
debug1: permanently_set_uid: 111/65534                                                                                                                                              
debug1: list_hostkey_types: ssh-rsa,ssh-dss                                                                                                                                         
debug1: SSH2_MSG_KEXINIT sent                                                                                                                                                       
debug1: SSH2_MSG_KEXINIT received                                                                                                                                                   
debug1: kex: client->server aes128-cbc hmac-md5 none                                                                                                                                
debug1: kex: server->client aes128-cbc hmac-md5 none                                                                                                                                
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST received                                                                                                                                        
debug1: SSH2_MSG_KEX_DH_GEX_GROUP sent                                                                                                                                              
debug1: expecting SSH2_MSG_KEX_DH_GEX_INIT                                                                                                                                          
debug1: SSH2_MSG_KEX_DH_GEX_REPLY sent                                                                                                                                              
debug1: SSH2_MSG_NEWKEYS sent                                                                                                                                                       
debug1: expecting SSH2_MSG_NEWKEYS                                                                                                                                                  
debug1: SSH2_MSG_NEWKEYS received                                                                                                                                                   
debug1: KEX done
debug1: userauth-request for user <username> service ssh-connection method none
debug1: attempt 0 failures 0
debug1: PAM: initializing for "<username>"
debug1: PAM: setting PAM_RHOST to "localhost"
debug1: PAM: setting PAM_TTY to "ssh"
Failed none for <username> from ::1 port 45195 ssh2
debug1: userauth-request for user <username> service ssh-connection method password
debug1: attempt 1 failures 0
debug1: PAM: password authentication accepted for <username>
debug1: do_pam_account: called
Accepted password for <username> from ::1 port 45195 ssh2
debug1: monitor_child_preauth: <username> has been authenticated by privileged process
debug1: PAM: establishing credentials
User child is on pid 13481
debug1: SELinux support disabled
debug1: PAM: establishing credentials
debug1: permanently_set_uid: 1000/1000
debug1: Entering interactive session for SSH2.
debug1: server_init_dispatch_20
debug1: server_input_channel_open: ctype session rchan 0 win 1048576 max 16384
debug1: input_session_request
debug1: channel 0: new [server-session]
debug1: session_new: session 0
debug1: session_open: channel 0
debug1: session_open: session 0: link with channel 0
debug1: server_input_channel_open: confirm session
debug1: server_input_global_request: rtype no-more-sessions@openssh.com want_reply 0
debug1: server_input_channel_req: channel 0 request pty-req reply 1
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req pty-req
debug1: Allocating pty.
debug1: session_new: session 0
debug1: SELinux support disabled
debug1: session_pty_req: session 0 alloc /dev/pts/3
debug1: server_input_channel_req: channel 0 request env reply 0
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req env
debug1: server_input_channel_req: channel 0 request shell reply 1
debug1: session_by_channel: session 0 channel 0
debug1: session_input_channel_req: session 0 req shell
debug1: Setting controlling tty using TIOCSCTTY.
```

---


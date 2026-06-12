---
title: "prftpd"
date: 2005-05-05
forum: Server Platforms
---

### Post by jayd36108 on 2005-05-05
can someone help me configure proftpd so i can ftp files from another computer onto the ubuntu computer that will serve my websites?

---

### Post by alastair on 2005-05-05
Here :

 - Read the docs. There is usually documentation under /usr/share/doc/<program>
 - See the "man" page (e.g. man proftpd ?)
 - Check [http://www.proftpd.org/docs/](http://www.proftpd.org/docs/)
 - Make sure the FTP daemon is running - check its LOG files for messages/errors etc.

Come back with specific problems you hit.

---

### Post by jayd36108 on 2005-05-05
my problem is i get a connect failure error message on my coputer i want to ftp files from

here is my config file
[I]

ServerName			"media"
ServerType			standalone
DeferWelcome			off

ShowSymlinks			on
MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on
AllowOverwrite			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
LsDefaultOptions                "-l"

# Port 21 is the standard FTP port.
Port				21

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User				nobody
Group				nogroup

# Normally, we want files to be overwriteable.
<Directory /*>
  AllowOverwrite		on
</Directory>

# A basic anonymous configuration, no upload directories.

<Anonymous /home/ftp>
  # All files uploaded are set to username.usergroup ownership
  User jay
  Group root
  UserAlias ftp username
  AuthAliasOnly on
  RequireValidShell off

  <Directory pub/incoming/>
     <Limit STOR CWD>
        AllowAll
     </Limit>
     <Limit READ RMD DELE MKD>
        DenyAll
     </Limit>
  </Directory>
</Anonymous>
          [/I]

---

### Post by lt_kije on 2005-05-10
If you run the site and all you need to do is copy files over, I'd recommend using sftp (including in openssh-server). That's terribly easy to set up and use and is encrypted to boot. If you have openssh-server installed and sshd is running, sftp connections can be made from remote hosts using the sftp command. Windows users can download PuTTY's excellent psftp app as well.

lt_kije

---


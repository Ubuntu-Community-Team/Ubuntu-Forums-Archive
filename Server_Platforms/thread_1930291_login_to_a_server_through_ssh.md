---
title: "login to a server through ssh"
date: 2012-02-23
forum: Server Platforms
---

### Post by 1cookie on 2012-02-23
hi

I'm trying to login to a remote server via ssh. At the terminal I type:
```

$ ssh -p username@host.co.uk
Bad port 'username@host.co.uk'

```but get the error as shown above. 

Ive done a ssh --help but it's pretty cryptic stuff. Ive tried different switches with combinations:


```

[-1246AaCfgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-e escape_char] [-F configfile]
           [-I pkcs11] [-i identity_file]
           [-L [bind_address:]port:host:hostport]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-R [bind_address:]port:host:hostport] [-S ctl_path]
           [-W host:port] [-w local_tun[:remote_tun]]
           [user@]hostname [command]


```
Can anyone help with this simple login process?

---

### Post by spynappels on 2012-02-23
If the SSH server is on port 22 (default), you can just use

```
ssh username@server
```

else you need to specify the port

```
ssh username@server -p portno
```

or just 
```
ssh username@server:portno
```

---

### Post by CharlesA on 2012-02-23
You don't need to use -p unless you are specifying a port other than 22.

EDIT: Ninja'd by spynappels ;)

---

### Post by 1cookie on 2012-02-23
> **spynappels said:**
> If the SSH server is on port 22 (default), you can just use

```
ssh username@server
```else you need to specify the port

```
ssh username@server -p portno
```or just 
```
ssh username@server:portno
```


I'm now logged in thanks and yes, I'm using a different port number.

---

### Post by spynappels on 2012-02-23
Cool 1cookie, glad it works for you!

Not often I get the first answer in CharlesA! I must be the slowest ninja on earth...

---

### Post by 1cookie on 2012-02-23
> **spynappels said:**
> Cool 1cookie, glad it works for you!

Not often I get the first answer in CharlesA! I must be the slowest ninja on earth...

Can I pick your brains further. I now want to copy a file from the remote host to my desktop say. I'm logged in and try:

```

cp file.txt ~/Desktop

```No file appears on my desktop though?

---

### Post by Lars Noodén on 2012-02-23
It should be something like this:

```

scp user@remotehost:file.txt ~/Desktop/.

```

That will copy the file from the remote server to your local desktop using [scp](http://manpages.ubuntu.com/manpages/oneiric/en/man1/scp.1.html).  Check the manual page for the details.

---

### Post by 1cookie on 2012-02-23
> **Lars Noodén said:**
> It should be something like this:

```

scp user@remotehost:file.txt ~/Desktop/.

```That will copy the file from the remote server to your local desktop using [scp]("http://manpages.ubuntu.com/manpages/oneiric/en/man1/scp.1.html").  Check the manual page for the details.

hi

I'm using absolute paths to reference files on the remote host:
```

[admin@remotehost /usr/local/www/apache/mydomain.co.uk/htdocs]$ scp admin@remotehost.co.uk:/usr/local/www/apache/mydomain.co.uk/htdocs/index.php ~/Desktop/.
Password:
/home/admin/Desktop/.: Not a directory


```No file on the desktop.

Ive made a simple mistake somewhere?

---

### Post by spynappels on 2012-02-23
> **1cookie said:**
> hi

I'm using absolute paths to reference files on the remote host:
```

[admin@remotehost /usr/local/www/apache/mydomain.co.uk/htdocs]$ scp admin@remotehost.co.uk:/usr/local/www/apache/mydomain.co.uk/htdocs/index.php ~/Desktop/.
Password:
/home/admin/Desktop/.: Not a directory


```No file on the desktop.

Ive made a simple mistake somewhere?

If you just want to copy the index.php file to your desktop, use the command above but leave off the full stop (.) after ~/Desktop/

---

### Post by kevdog on 2012-02-23
Nothing is wrong with scp, however I really find working with sftp (which works with ssh -- not ftp as you might think), is a lot easier -- if you want to do something interactively.  It uses much of the same commands as get/put that you are used to using with ftp.  scp is good if you want to automate things.  Usually however if I'm going to be doing a lot of file transfers repetitively I usually just use rsync.

---

### Post by 1cookie on 2012-02-24
> **kevdog said:**
> Nothing is wrong with scp, however I really find working with sftp (which works with ssh -- not ftp as you might think), is a lot easier -- if you want to do something interactively. 

Thanks guys. Yes I'm trying to upload/download files from a public facing server using SSH, and the Terminal. For simplicity I would normally do this through an FTP client FileZilla say, but find myself doing it a more 'grown up' way if you will.

The problems continue for now though, as now I cannot login through SSH from home. I'm on a wireless network behind a router with dynamic IP address in the UK. Does dynamic IP addressing affect a SSH session?

---

### Post by Lars Noodén on 2012-02-24
> **1cookie said:**
> Does dynamic IP addressing affect a SSH session?

Not for outbound connections.  But if the server you are trying to connect to is using or behind a dynamic IP address, then there are some additional hoops to hop through.  One way that works (for the most part) would be to use a [dynamic DNS service](https://help.ubuntu.com/community/DynamicDNS) to map the ever-changing 
number to a static name.

---

### Post by spynappels on 2012-02-24
Hi 1cookie, you can use SFTP from Filezilla, just use SFTP and port 22 in Connection Manager.

As for connecting from outside the LAN, that should be ok if the router is set to forward port 22 to the server, or if the server is directly connected, the firewall in the server is set to allow access from external IPs.

Connecting from a dynamically assigned IP should not be a problem. What sort of errors are you seeing?

---

### Post by 1cookie on 2012-02-24
> **spynappels said:**
> Hi 1cookie, you can use SFTP from Filezilla, just use SFTP and port 22 in Connection Manager.

Connecting from a dynamically assigned IP should not be a problem. What sort of errors are you seeing?

hi

I managed to login from home last night so there shouldn't be a problem. From the terminal:

```

andy@andy-R519-R719:~$ ssh host.co.uk -p 12345
Password:
Password:
Password:
Permission denied (publickey,keyboard-interactive).




```
EDIT:
what a noob, I forgot my username. 

```
 ssh user@host.co.uk -p 12345
```thanks for all the help and the insight....:)

---

### Post by spynappels on 2012-02-24
> **1cookie said:**
> 
```

andy@andy-R519-R719:~$ ssh host.co.uk -p 12345
Password:
Password:
Password:
Permission denied (publickey,keyboard-interactive).


```

That's an authentication problem, connectivity is ok or you would not even get to that point.

I presume you're sure that the password is correct, and that andy is the correct user on the remote server,but you might want to check your keyboard mappings, if your password has "unusual" characters like @!$% etc, check your keyboard is mapped correctly and you are actually entering what you think you are entering, not seeing the password on the screen means you might accidentally be typing the wrong password.

Of course, using publickey authentication would do away with that problem...

---

### Post by 1cookie on 2012-02-24
> **spynappels said:**
> Hi 1cookie, you can use SFTP from Filezilla, just use SFTP and port 22 in Connection Manager.


hi 

Just to pick you up on this point. Are you referring to the 'Open Site Manager' option in FileZilla?

---

### Post by spynappels on 2012-02-24
> **1cookie said:**
> hi 

Just to pick you up on this point. Are you referring to the 'Open Site Manager' option in FileZilla?

Ctrl+S will open the Site Manager, you can then enter new connection details and it allows you to specify the protocol.

Not looked at Linux FileZilla though, so it *might* be different...

---

### Post by 1cookie on 2012-02-24
> **spynappels said:**
> Ctrl+S will open the Site Manager, you can then enter new connection details and it allows you to specify the protocol.

Not looked at Linux FileZilla though, so it *might* be different...

That's worth a look, thanks. Lets say I want to copy an entire directory (htdocs) from the server to my desktop through SSH. Is my best option scp?

```

[admin@remotehost /usr/local/www/apache/mydomain.co.uk/htdocs]$ scp admin@remotehost.co.uk:/usr/local/www/apache/mydomain.co.uk/htdocs ~/Desktop/


```

---

### Post by 1cookie on 2012-02-24
SFTP through FileZilla and I can see the entire server graphically...that's nice.

Thanks for the help...:)

---

### Post by Lars Noodén on 2012-02-24
For copying an entire directory, I would use [rsync](http://manpages.ubuntu.com/manpages/oneiric/en/man1/rsync.1.html) which in turn uses SSH.

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by spynappels on 2012-02-24
> **1cookie said:**
> SFTP through FileZilla and I can see the entire server graphically...that's nice.

Thanks for the help...:)

I presume that means you've been able to get in to the remote server from home?;)

---

### Post by CharlesA on 2012-02-24
> **Lars Noodén said:**
> For copying an entire directory, I would use [rsync](http://manpages.ubuntu.com/manpages/oneiric/en/man1/rsync.1.html) which in turn uses SSH.

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
+1 to rsync. I've been using it instead of scp even if I need to copy just one file.

---


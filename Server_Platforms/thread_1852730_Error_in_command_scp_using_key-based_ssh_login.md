---
title: "Error in command scp using key-based ssh login"
date: 2011-09-30
forum: Server Platforms
---

### Post by asm2545w on 2011-09-30
Hi guys,

I have a problem that I can't resolve.

I have an ubuntu server 11.04 at home with openshh installed (minimal installation). I use rsa key-based ssh login to connect to the server (I disabled the password authentication in the sshd_config). I can connect to the server, update and upgrade, etc..., but when I trying to copy a file from the server to the client (ubuntu desktop 10.04) using scp I get this error:

server:~$ scp -r user@ip_server:/home/user/Desktop/file user@ip_client:/home/user/Desktop
The authenticity of host 'ip_server (ip_server)' can't be established.
ECDSA key fingerprint is fc:0b:dd:0e:42:85:fc:25...
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'ip_server' (ECDSA) to the list of known hosts.
Permission denied (publickey).

I edited the file known_hosts in the client, but I do not know what I can do it.

Any idea?

Thanks in advance,

  Alvaro

---

### Post by volkswagner on 2011-09-30
You wrote:

```
server:~$ scp -r user@ip_server:/home/user/Desktop/file user@ip_client:/home/user/Desktop
```

Is "user@ip_server:/home/user/Desktop/file" the same location as "server:~$"?

Where do you have keys setup (between which machines)?

Can you ssh into "user@ip_server:/home/user/Desktop/" then use scp?

```
ip_server:~$ scp -r Desktop/file user@ip_client:/home/user/Desktop
```

If the first two servers are the same machine the second command should be what you need directly ignore the ssh into second server.

---

### Post by hawkmage on 2011-09-30
First of all scp will not copy from and to remote systems in the came command.  Scp will assume a source or destination includes host: will be considered a remote system.  

Do you have the client accounts ssh public key in the authorized_keys of the user on the server that you are copying from?

---

### Post by asm2545w on 2011-10-01
> **volkswagner said:**
> You wrote:

```
server:~$ scp -r user@ip_server:/home/user/Desktop/file user@ip_client:/home/user/Desktop
```

Is "user@ip_server:/home/user/Desktop/file" the same location as "server:~$"?

Where do you have keys setup (between which machines)?

Can you ssh into "user@ip_server:/home/user/Desktop/" then use scp?

```
ip_server:~$ scp -r Desktop/file user@ip_client:/home/user/Desktop
```

If the first two servers are the same machine the second command should be what you need directly ignore the ssh into second server.

Is "user@ip_server:/home/user/Desktop/file" the same location as "server:~$"?

I was wrong, the file in the server was in /home/user, not in /home/user/Desktop. I did not install a desktop in the server (only command line).

Where do you have keys setup (between which machines)?

Not exactly what you mean. I generated the keys in the client and transfer them to the server.

Can you ssh into "user@ip_server:/home/user/Desktop/" then use scp?

When I try: (forget Desktop directory)

$ ssh user@ip_server:/home/user

I get this message:

ssh: Could not resolve hostname ip_server:/home/user: Name of service not known


> **hawkmage said:**
> First of all scp will not copy from and to remote systems in the came command.  Scp will assume a source or destination includes host: will be considered a remote system.  

Do you have the client accounts ssh public key in the authorized_keys of the user on the server that you are copying from?

What do you mean exactly? I generated the rsa keys in the client and transfer them to the server.

---

### Post by asm2545w on 2011-10-01
Well, I am going to write what exactly I did after install a normal installation of Ubuntu Server 11.04 with openssh:

All as a root:
$ sudo -s

First update and upgrade repositories:		
$ apt-get update
$ apt-get upgrade

Install and configure firewall:					
$ apt-get install ufw
$ ufw allow 22

Block every connection except port 22 (ssh):	
$ ufw enable	
$ ufw limit 22

Network configuration (edit /etc/network/interfaces and add):				$ sudo vim /etc/network/interfaces
				
auto eth0
iface eth0 inet static
address ip_server
netmask ip_mask
gateway ip_gateway

Use Key-Based SSH Logins:
	
Generating RSA keys in the client:	
$ ssh-keygen -t rsa -b 4096

Transfer Client Key to Host (from client):	
**$ ssh-copy-id user@ip_server**

And this is only what I did. I followed these to tutorials:

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Key-Based_SSH_Logins](https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Key-Based_SSH_Logins)

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#disable-password-authentication](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#disable-password-authentication)

In this point I can connect to the server from the client (ubuntu desktop 10.04) via ssh with this command:

$ ssh user@ip_server

The system will ask me for a passphrase. I can update and upgrade the server, install new software, etc..., but I cannot use the command scp properly.

When I try:

$ ssh user@ip_server:/home/user/Desktop

I get this message:

ssh: Could not resolve hostname ip_server:/home/user/Desktop: Name of service not known


Back to the problem, the command I am trying is this:

Connect to the server from the client:
$ ssh user@ip_server
user@server:~$ scp file user@ip_client:/home/user/Desktop

I created a file called "file" in the user_home directory in the server, and I am trying to copy the file to the Desktop in the client. Now I get this message:

ssh: connect to host ip_client port 22: Connection timed out
lost connection

If I try this other command from the server:
user@server:~$ scp user@ip_server:/home/user/file user@ip_client:/home/user/Desktop

Now I get:

Permission denied (publickey)


What do you think?

---

### Post by volkswagner on 2011-10-01
Well I'm still a little confused.

I'm going to assume my first assumption is correct:  There is only one server and one client.  There fore you should not have to @ in you scp command.

Does you client allow ssh connection.

Try ssh to server and back to client.  If you have easy physical access to server, just sit at console and see if you can ssh into it.

Or from the client do a daisy chain ssh connection.
```
ssh user@server_ip
```

Then once the ssh connection is working you will be at a prompt from the server and try to ssh back into the client to see if your firewall or if sshserver deamon is receiving connections.

```
ssh user@client_ip
```



Also:  When using ssh command don't add the trailing directory just use "ssh user@machine_ip", this way you won't get host unresolved error.
Note2:  I don't think the ssh_key login is a two way protocol.  If you setup keyed login to the server and it is working, you need to repeat the steps to get keyed login to the client from the server.

---

### Post by asm2545w on 2011-10-01
Now I am not at home, but I will try tonight. I think you have clarified me the problem.

Thanks a lot for your time.

PS you were right, there is only one server and one client

---

### Post by asm2545w on 2011-10-03
Well, finally I have resolved the problem. You were right Volkswagner, key-based ssh login is not a two ways protocol.

So, what I did, uninstall ssh in client and server:

$ sudo apt-get remove openssh-client
$ sudo apt-get remove openssh-server

Also delete in both machines these directories:

/etc/ssh
/home/user/.ssh

Then, I installed ssh client and server in both machines:

$ sudo apt-get install openssh-client
$ sudo apt-get install openssh-server

After, setup key-based ssh login in both machines:

From client:
    Generating RSA keys:
        $ ssh-keygen -t rsa -b 4096
    Transfer Client Key to Server:			
        $ ssh-copy-id user@ip_server
    Protect authentication_keys file:			
        $ chmod 600 .ssh/authorized_keys

From server:
    Generating RSA keys:			
        $ ssh-keygen -t rsa -b 4096
    Transfer Server Key to Client:			
        $ ssh-copy-id user@ip_client
    Protect authentication_keys file:			
        $ chmod 600 .ssh/authorized_keys

Finally, disable password authentication in both machines, edit /etc/ssh/sshd_config and look for the following line

#PasswordAuthentication yes

and change it for:  PasswordAuthentication no

Now, the command scp works fine.

Thanks everyone

---

### Post by asm2545w on 2011-10-03
How can I mark this thread as SOLVED?

---

### Post by volkswagner on 2011-10-03
At the top of the thread select "Thread Tools" > "mark solved".

Glad you got it working.

:)

---

### Post by asm2545w on 2011-10-05
Thanks again mate

---


---
title: "tftp server"
date: 2008-05-02
forum: Server Platforms
---

### Post by dachinster on 2008-05-02
Hi guys,
I am trying to setup a tftp server.
Edit: Running Ubuntu 8.04 Server

Here is the output of /etc/xinetd.d/tftp
[I]root@ubuntutftp:/home/dachinster# cat /etc/xinetd.d/tftp 
service tftp
{
protocol        = udp
port            = 69
socket_type     = dgram
wait            = yes
user            = nobody
server          = /usr/sbin/in.tftpd
server_args     = -s /tftp/
disable         = no
}[/I]

ls -la /  gives:
*drwxrwxrwx   2 nobody root  4096 2008-05-02 14:02 tftp*

and ls -la /tftp  gives:
[I]root@ubuntutftp:/home/dachinster# ls -la /tftp
total 12
drwxrwxrwx  2 nobody root     4096 2008-05-02 14:02 .
drwxr-xr-x 22 root   root     4096 2008-05-02 12:41 ..
-rwxrwxrwx  1 nobody dachinster   27 2008-05-02 14:02 test2.txt[/I]

My problem is that when I do:
[I]tftp 10.0.9.20
tftp> binary
tftp> put test2.txt[/I]

I get this:
[B]tftp: test2.txt: No such file or directory

[/B]However, if I create another file in my /home directory named hda.txt for instance and i say:
put hda.txt
I will see the file transfer across

The problem is that I want the server to read and write to the folder /tftp

Any idea how to accomplish that?

---

### Post by AmirKamal73 on 2008-05-04
Hi,

I also had the same problem. In order to get this working, I tried to set the current directory to the one mentioned in the server_args and then did the tftp. In that way it worked.


For my case, the directory I set in server_args: -s /tftpboot/

I also saved my hda.txt file in that same directory.
Now try to do the tftp from this directory and then put the file.
It should work.

Happy trying!!

---

### Post by dachinster on 2008-05-05
hmmm,
Peculiar!
I changed it to -s /tftpboot/
It worked!
Then I changed it back to -s /tftp/
Then it started working with this too.... very strange

Thanks! :)

---

### Post by dachinster on 2008-05-06
Ok
Now that I have the TFTP server up and running, I would like to create a separate log file to log each and every connection attempt and the file downloaded. 
Also, I need to know the IP address of the machine that connects to it and requests the file along with the name of the file
How do I go about doing this? Is this possible?

---


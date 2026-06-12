---
title: "Apache settings"
date: 2008-09-08
forum: Server Platforms
---

### Post by ub007 on 2008-09-08
I have setup an intranet of 10 machines(all running Ubuntu).
I have created a browser interface under Apache web server that would connect to any of the machines in the intranet via ssh.The code is in PHP.

Since it is not good idea to keep the SSH  password in PHP script, or even allowing user to pass it though WEB interface,thought it is better to keep all user names, passwords and servers IPs in some settings.ini file

> [server1]
ip = 'A.B.C.D:PORT'
user = 'some_name'
pass = 'some_pass'

[server2]
ip = 'A.B.C.D:PORT'
user = 'some_name'
pass = 'some_pass'
> 
I need to disable the direct access of that file from the URL [http://example.com/pcmanager/settings.ini](http://example.com/pcmanager/settings.ini). 

How do i accomplish this?
Some one suggested .htaccess.....,but how do i implement it?

I created a .htaccess file in /var/www with th foll code

Code:

RewriteEngine on
RewriteBase /
RewriteRule ^settings.ini$ - [F]

But i do not know whether and what changes i need to make in the apache conf files....so at the moment i can still access it from [http://example.com/pcmanager/settings.ini](http://example.com/pcmanager/settings.ini).

Plz help.i would like only apache to have access to this file and no other users.....

---

### Post by cdenley on 2008-09-08
> **ub007 said:**
> I have setup an intranet of 10 machines(all running Ubuntu).
I have created a browser interface under Apache web server that would connect to any of the machines in the intranet via ssh.The code is in PHP.

Since it is not good idea to keep the SSH  password in PHP script, or even allowing user to pass it though WEB interface,thought it is better to keep all user names, passwords and servers IPs in some settings.ini file


 

How do i accomplish this?
Some one suggested .htaccess.....,but how do i implement it?

I created a .htaccess file in /var/www with th foll code

Code:

RewriteEngine on
RewriteBase /
RewriteRule ^settings.ini$ - [F]

But i do not know whether and what changes i need to make in the apache conf files....so at the moment i can still access it from [http://example.com/pcmanager/settings.ini](http://example.com/pcmanager/settings.ini).

Plz help.i would like only apache to have access to this file and no other users.....

So you want a php script to login to a remote ssh server? No matter where you store the passwords, if your php script knows the password, it isn't a very secure solution. I think the idea of storing the password in a seperate file would be to put the file in a directory which isn't available through apache, but your script can read it since it has access to the local filesystem. However, I don't think this would be much more secure. If an attacker manages to read your source code, they will probably be able to open your settings.ini file too.

What are you trying to accomplish with this, anyway?

---

### Post by ub007 on 2008-09-08
> So you want a php script to login to a remote ssh server? 

No,I already have coded it-
> $machineValues = array("192.168.11.30", "root", "password","david", "
192.168.11.19", "root", "password2","david2", "192.168.11.32", "root2",
"password3","david3");// log in at server1.example.com on port 22
if (!function_exists("ssh2_connect")) die("function ssh2_connect doesn't
exist");
// log in at server1.example.com on port 22

for ( $counter = 0; $counter < sizeof($machineValues); $counter =
$counter+4) {
if($number_of_machines<$number){

if(!($con = ssh2_connect($machineValues[$counter], 22))){
echo "fail: unable to establish connection\n";
echo "Machine number $counter is $machineValues[$counter]";
} else {
// try to authenticate with username root, password secretpassword
    if(!ssh2_auth_password($con, $machineValues[$counter+1],
$machineValues[$counter+2])) {
      echo "fail: unable to authenticate\n";
    } else {
           echo "okay: logged in...\n";
       // execute a command


> I think the idea of storing the password in a seperate file would be to put the file in a directory which isn't available through apache, but your script can read it since it has access to the local filesystem.

yes,thats exactly what i need.
I would have a web browser interface with a form,thats all the user should have access to-like [www.192.168.11.21/pc_control.php](www.192.168.11.21/pc_control.php)  //this contains a form where user fills in his details and programs to execute and so on,and hits the submit button...
pc_control.php calls another php script-say action.php which will ssh into the remote machine and execute commands....since there are many servers and programs,i intend to have it in another file settings.ini //action.php reads from it

i wish to secure settings.ini //i know its limited security,but still helps.....
if i do so,no no one can access it [http://192.168.11.22/settings.ini](http://192.168.11.22/settings.ini)
At the same time i need apache to be able to access it

---

### Post by cdenley on 2008-09-08
Well, if your scripts are in /var/www, put the configuration file anywhere else, such as /etc/mysettings/login.php.

Store your login information in login.php like
[PHP]
<?php
$user="myuser";
$pass="mypass";
?>
[/PHP]

Then in your scripts which need access to the username and password, use this line
[PHP]
<?php
@include("/etc/mysettings/login.php");
?>
[/PHP]
Then you would be able to access the variables from the file login.php. I don't think this would be a significant improvement in security, though.

---

### Post by ub007 on 2008-09-08
Would it be better if i used key based login?
i tried that ,but the code didnt work,i thought apache wasnt able to read from .ssh directory....wondering how i could give apache permissions to read from .ssh....

---

### Post by cdenley on 2008-09-08
> **ub007 said:**
> Would it be better if i used key based login?
i tried that ,but the code didnt work,i thought apache wasnt able to read from .ssh directory....wondering how i could give apache permissions to read from .ssh....

I'm not sure if that would be better, since that would allow the apache user to connect to your server without a password under any circumstance. That means if apache or a script is compromised, and an attacker gains shell access, they will also have shell access to your SSH server. Of course if they can read your passwords anyway, it doesn't make much of a difference. Either way, it isn't very secure.

I think if I needed my web server to run a command on a remote server, I would setup a simple server on the remote server that listens for connections from the web server. When the connection is established, run the command, then exit. This ensures the web server doesn't have any more access than is necessary. I did something like this so my web server could tell my firewall to update it's rules. Does the server running the command also have apache with php?

---


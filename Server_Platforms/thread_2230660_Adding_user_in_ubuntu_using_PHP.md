---
title: "Adding user in ubuntu using PHP"
date: 2014-06-20
forum: Server Platforms
---

### Post by Rohit_Gupta on 2014-06-20
I am trying to add user to my Ubuntu Virtual Machine (Microsoft Azure) using PHP from another server.

Here is my code.

[PHP]
<?php
//including phpseclib
include('Net/SSH2.php');

//Username and Password from form
$username = $_POST['user'];
$password = $_POST['pass'];

//connecting to azure vm using ssh
$ssh = new Net_SSH2('myservername.cloudapp.net:22');
$ssh->login('myuserid', 'mypassword') or die("Login failed");
$ssh->getServerPublicHostKey();
$cmd = "sudo useradd -d /home/$username -p $(perl -e'print crypt(\"$password\", \"cu\")') $username";
$cmdr = $ssh->exec($cmd);
?>
[/PHP]

The user is created successfully, but when I login to the server using putty it shows "Access Denied"

Kindly help, where am I going wrong?

---

### Post by DJ_Max on 2014-06-21
First I would sanitize your POST variables.

Second, why are you running a perl command inside a PHP script?

When you say you login to the server, are you actually logged in, or can you not authenicate? First thing I would check is to make sure your password hash isn't getting changed on execution.

---

### Post by lisati on 2014-06-21
I'd also look at avoiding the use of commands which require sudo where possible, otherwise you'll need to make sure that your server is tightened up against attacks by injection into scripts.

---

### Post by Rohit_Gupta on 2014-06-22
Don't worry about the POST variable... its only for the testing phase... I will allocate them the login Userid & Pass...

I am using perl because -p parameter should contain the encrypted password and i m encrypting the password using perl crypt..

I am sure that the problem is with this perl section only... the hash generated in the php is not matching with the password hash at the time of login.

Any alternative to use this -p parameter....????

---

### Post by Rohit_Gupta on 2014-06-22
[COLOR=#000000][FONT=Arial]It's done...!![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Here is the final PHP code
[/FONT][/COLOR]
[PHP]include('Net/SSH2.php');

//Username and Password from form
$username = $_POST['user'];
$password = $_POST['pass'];
$salt = "12345678" //any random 8 digit

//connecting to azure vm using ssh
$ssh = new Net_SSH2('myservername.cloudapp.net:22');
$ssh->login('myuserid', 'mypassword') or die("Login failed");
$ssh->getServerPublicHostKey();
$cmd = "sudo useradd -m -p $(mkpasswd -m sha-512 $password $salt) $username";
$cmdr = $ssh->exec($cmd);[/PHP]

[COLOR=#000000][FONT=Arial]Solved.![/FONT][/COLOR]

---

### Post by SeijiSensei on 2014-06-23
And how, may I ask, did you deal with the permissions problem?  I hope you didn't give the www-data user sudo rights.  If so, I would expect someone other than you to own this machine in the months ahead.  The whole design of programs like Apache is to avoid the need for the owner of the server process to have root privileges.  If you grant the www-data user sudo privileges, you've just destroyed the security model underpinning the server software.

---


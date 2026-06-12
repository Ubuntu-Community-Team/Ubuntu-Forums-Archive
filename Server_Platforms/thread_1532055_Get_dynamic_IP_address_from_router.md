---
title: "Get dynamic IP address from router"
date: 2010-07-15
forum: Server Platforms
---

### Post by mlinux on 2010-07-15
I need to obtain daily dynamic IP address from my router for remote user. In order to get into the router page, I need to login to it with ID and password.

Can I tell the server to do this every time it started up to login to router and extract the ip address and send out via email?

The router can only access through web interface and below is what I copied from browser. 

=================================================
Overall Status
ADSL Line Status: 	SHOWTIME
Downstream Data Rate: 	3488kbps
Upstream Data Rate: 	640kbps

PPP Connection Status: 	Connected
Protocol & Encapsulation Mode: 	PPPoA VC-Mux
VPI/VCI: 	0/100
 
WAN Statistic:

IP Address	Subnet Mask	MAC Address
210.193.xxx.xxx	255.255.255.0	00:30:0A:09:78:0B

LAN Statistic:
Number of computers connected to the DHCP server: 
===================================================

---

### Post by volkswagner on 2010-07-16
An alternative could be to setup an account at [noip.com]("http://www.no-ip.com/").

You will choose a domain name you can distribute.  You then use the linux update client on your server, to update your ip address.  This way you will still have access after the ipaddress changes, and use the same domain name.

---

### Post by mlinux on 2010-07-18
> **volkswagner said:**
> An alternative could be to setup an account at [noip.com]("http://www.no-ip.com/").

You will choose a domain name you can distribute.  You then use the linux update client on your server, to update your ip address.  This way you will still have access after the ipaddress changes, and use the same domain name.

Thanks for the advise. 

My intention is to grab the dynamic IP from the router and upload it to existing website hosted by the isp. In this way, user just need to visit the exiting website, click the link to access to this dynamic ip server which will be turned on during office hour only.

---

### Post by mlinux on 2010-07-23
After many days of searching, found the solution using the follow php script. I uploaded it to existing remote webserver and it is working when direct link using web browser from PC, I get the dynamic ip in my email.

Question is how to put a url link in local php script so that when execute the local php script in command line mode from local server, it will run the php script in the remote webserver.

[PHP]<?php
// get my dynamic ip address
$user->emailAddr = 'xxxx@xxxx.com';
$ip=$_SERVER['REMOTE_ADDR'];

//echo '<p>Thank You</p>';

//echo '<p>The IP address is '.$ip.'</p>';

$message = 'The IP address is '. $ip ;

if (@mail($user->emailAddr, 'IP address', $message))
{
//  echo 'It has been send to ' . $user->emailAddr  ;
}
else
{
//  echo 'Problem sending ip address';
}
?>
[/PHP]

---

### Post by lisati on 2010-07-23
You might want to arrange for the PHP script **from** the machine whose IP address you want to discover. One way might be to organize a CRON job on the server to invoke php5-cli to run the script.

---

### Post by mlinux on 2010-07-23
You can not ask the remote webserver to execute php on it own. The request has to come from the PC/server behind the "router" in order to know your router wan address.

---

### Post by mlinux on 2010-07-26
Before arrange a CRON job in local server, I need to have a php script on local server. However, no luck so far to get the following script to work. No error messages from php-cli, no response from external server. Anyone know the reason?

[PHP]<?php
header('Location: http://www.xxx.com/xxx/get_my_dynamic_addr.php');
?>[/PHP]

---

### Post by Bachstelze on 2010-07-26
> **mlinux said:**
> Before arrange a CRON job in local server, I need to have a php script on local server.

Nah, just [font=monospace]wget[/font] it. ;)

---

### Post by mlinux on 2010-07-26
> **Bachstelze said:**
> Nah, just [font=monospace]wget[/font] it. ;)

Thanks Bachstelze, I use the wget -q option and I am ready to add this to startup and moving on to my web construction.

---


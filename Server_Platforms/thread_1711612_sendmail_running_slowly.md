---
title: "sendmail running slowly"
date: 2011-03-21
forum: Server Platforms
---

### Post by bigmonmulgrew on 2011-03-21
Hi guys.
I've been experimenting with setting up a web server over the last few weeks. This week I've been trying to create a contacts page using php. The emails werent getting sent though.
At first it wouldnt work and after a lot of googling I eventually installed exim4 and sendmail.

Now when rebooting the server it hangs on 
Starting MTA for quite a while (maybe a minute) The server previously took under 10 seconds to boot.

Also when clicking submit on the coontact form it sits wirring away for aaround a minute before finally sending the email.

The test pages are at
[www.mulgrewenterprises.co.uk/samplemail.php](www.mulgrewenterprises.co.uk/samplemail.php) and
[www.mulgrewenterprises.co.uk/contacts.php](www.mulgrewenterprises.co.uk/contacts.php)

but in case it changes as I'm updating it the code is below.
Doubt its the code though as I've tried a few other methods and they all sit wirring away for about a minute. (Some work others do not)

Could I have done something wrong installing exim4 or sendmail.
```
<?php
/*
From http://www.html-form-guide.com 
This is the simplest emailer one can have in PHP.
If this does not work, then the PHP email configuration is bad!
*/
$msg="";
if(isset($_POST['submit']))
{
    /* ****Important!****
    replace name@your-web-site.com below 
    with an email address that belongs to 
    the website where the script is uploaded.
    For example, if you are uploading this script to
    www.my-web-site.com, then an email like
    form@my-web-site.com is good.
    */

	$from_add = "info@mulgrwenterprises.co.uk"; 

	$to_add = "bigmonmulgrew@googemail.com"; //<-- put your yahoo/gmail email address here

	$subject = "Test Subject";
	$message = "Test Message";
	
	$headers = "To: $to_add \r\n";
	$headers = "From: $from_add \r\n";
	$headers .= "Reply-To: $from_add \r\n";
	$headers .= "Return-Path: $from_add\r\n";
	$headers .= "X-Mailer: PHP \r\n";
	
	
	if(mail($to_add,$subject,$message,$headers)) 
	{
		$msg = "Mail sent OK";
	} 
	else 
	{
 	   $msg = "Error sending email!";
	}
}
?>
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd"> 
<html>
<head>
	<title>Test form to email</title>
</head>

<body>
<?php echo $msg ?>
<p>
<form action='<?php echo htmlentities($_SERVER['PHP_SELF']); ?>' method='post'>
<input type='submit' name='submit' value='Submit'>
</form>
</p>


</body>
</html>
```

---

### Post by hictio on 2011-03-21
> **bigmonmulgrew said:**
> 
~snip~
Now when rebooting the server it hangs on 
Starting MTA for quite a while (maybe a minute) The server previously took under 10 seconds to boot.


I've seen those delays on Sendmail before, usually means a problem with your hostname or the DNS settings on the file "/etc/resolv.conf".
Does your server have a Fully Qualified Domain Name?

---

### Post by bigmonmulgrew on 2011-03-22
all it says in resolv.conf is

```
nameserverer 192.168.0.10
```

This is the IP address of my router to be clear.
What should it say in here?

---

### Post by hictio on 2011-03-22
> **bigmonmulgrew said:**
> all it says in resolv.conf is

```
nameserverer 192.168.0.10
```

This is the IP address of my router to be clear.
What should it say in here?

That looks Ok, it does work, right? If you type, for instance, ping [www.yahoo.es](www.yahoo.es) that work?

If so, which, it should, what is the hostname of you computer? Is it a real one registered on a DNS? If not, you might want to try adding your hostname to the /etc/hosts file to see if it solves your slowness problems.

---

### Post by bigmonmulgrew on 2011-03-22
I can indeed ping yahoo from the server and to my dismay then found out that simply using ping [www.yahoo.es](www.yahoo.es) would go forever
I should point out here that I'm well out of my depth in both my knowledge of linux and web servers in general.

The server is currently a virtual server hosted on my dektop PC, to be replaced by a real one as soon as I'm happy I know what I'm doing, or at least get it working well.
The server name is MEWebServer

the contents of the hosts file are below again I have no idea what this should be.

```
127.0.0.1	localhost
127.0.1.1	MEWebServer

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

---

### Post by hictio on 2011-03-22
> **bigmonmulgrew said:**
> I can indeed ping yahoo from the server and to my dismay then found out that simply using ping [www.yahoo.es](www.yahoo.es) would go forever

Ok, lets see this first.
Edit the file /etc/resolv.conf, add this:
```

nameserver 8.8.4.4
nameserver 8.8.8.8

```

Those are Google public DNS server, and they are fairly dependable.
After saving the file, try pinging sites that you haven't accessed yet, the important thing is that they resolv the hostname to IP addresses, that is that the DNS is actually working.

---

### Post by bigmonmulgrew on 2011-03-22
> **hictio said:**
> Ok, lets see this first.
Edit the file /etc/resolv.conf, add this:
```

nameserver 8.8.4.4
nameserver 8.8.8.8

```


I have added the above to resolv.conf

I then did
ping [www.ebay.co.uk](www.ebay.co.uk)

I get this output

```
PING hp-intl-uk.ebay.com (66.135.200.28) 56(84) bytes of data.
```

Then it sits there doing nothing. I've tried it with limiting the number of pings but I just get 100% packet loss

---

### Post by hictio on 2011-03-22
> **bigmonmulgrew said:**
> I have added the above to resolv.conf

I then did
ping [www.ebay.co.uk](www.ebay.co.uk)

I get this output

```
PING hp-intl-uk.ebay.com (66.135.200.28) 56(84) bytes of data.
```

Then it sits there doing nothing. I've tried it with limiting the number of pings but I just get 100% packet loss

I can't get a reply from them neither, pretty likely they are blocking ping requests, the important thing is that the hostname is resolving.
After editing the /etc/resolv.conf file have you tested sending an email thru Sendmail?

---

### Post by bigmonmulgrew on 2011-03-22
Yep just tried it took a fraction over a minute to send

---

### Post by hictio on 2011-03-22
> **bigmonmulgrew said:**
> Yep just tried it took a fraction over a minute to send

Are you sending the emails straight from you server? Or thru a SMART HOST of your ISP or similar?

---

### Post by bigmonmulgrew on 2011-03-22
not sure but straight from the server i think. Whatever the default is

---

### Post by hictio on 2011-03-22
Can you connect to the server via SSH to the CLI to do a couple of tests?
The delay happens with every address you have tested?

---

### Post by bigmonmulgrew on 2011-03-23
I dont usually bother with ssh. Its not necessary while I'm using a VPC but I did set it up anyway, just so I knew how and it does indeed work, just tested it again and it appears to be fine.

I've tested using several from and to addresses and 4 different sets of example php code, and one I wrote myself (not that mine would be any better). The delay happens with all of them

---


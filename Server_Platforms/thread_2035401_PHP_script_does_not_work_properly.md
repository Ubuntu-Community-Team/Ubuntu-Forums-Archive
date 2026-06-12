---
title: "PHP script does not work properly"
date: 2012-07-30
forum: Server Platforms
---

### Post by cocotu on 2012-07-30
Using Ubuntu 10.04.4 LTS. We run a php script that pulls info using XML from another server. We are not very familiar with XML. For example when we run:

php5 xmlrequest.php

We are supposed to get data from the other server and we see the output right on the terminal. We column names without the data. I have run:

sudo dpkg-reconfigure php5

And it worked. Not sure why. For the past week we have been trying the same solution, but it does not work anymore. We migrated from a shared server running CentOS to a VPS running Ubuntu. This is when issues started. Any suggestions? Help is very appreciated. Let me know if i am missing information. 

PHP version:
php5 -v
PHP 5.4.4-1~lucid+1 (cli) (built: Jun 17 2012 12:46:02) 
Copyright (c) 1997-2012 The PHP Group
Zend Engine v2.4.0, Copyright (c) 1998-2012 Zend Technologies
    with XCache v2.0.0, Copyright (c) 2005-2012, by mOo


Thanks.

---

### Post by BkkBonanza on 2012-07-30
You'll need to provide more info on script or script source here. Otherwise it's pretty unlikely anyone will have a clue why some script they're never seen doesn't work.

Any error messages spit out? Is this from the command line or running on a web server responding to requests.

I know PHP quite well and have coded web sites with it but that doesn't mean I can guess what's going wrong in your script.

---

### Post by cocotu on 2012-07-30
BkkBonaza, thanks for trying to help me. As I mentioned before the script works when I run: 
sudo dpkg-reconfigure php5

This makes me believe is a php configuration in this new vps server. It worked before we migrated to Ubuntu from CentOS.

1. This is from the command line.
2. NO error messages, I get the column names empty. This script gets stock status from a distributor in order to display in our shopping cart (we are using Magento).
3. Attached is the script.
4. Thanks for your help, I am not php savvy as you are.

If you need more details please let me know. Again, help is appreciated.

---

### Post by BkkBonanza on 2012-07-30
Just having a first look now. 

1. You know that there is a line near the top where you need to enter the server url (address)? The code as you gave me won't access the site without that.

2. It's using curl (a library for accessing the web) so you would have to make sure your install of PHP has that. I believe it's standard but you could use phpinfo to make sure curl is present.

3. Also appears username/password values need to be plugged into the script.

---

### Post by cocotu on 2012-07-31
1. As a stated before the code has worked many times in this Ubuntu server. I am hiding these values(sensitive stuff).

2. My phpinfo says:
> cURL support 	enabled
cURL Information 	7.19.7
Age 	3
Features
AsynchDNS 	No
Debug 	No
GSS-Negotiate 	Yes
IDN 	Yes
IPv6 	Yes
Largefile 	Yes
NTLM 	Yes
SPNEGO 	No
SSL 	Yes
SSPI 	No
krb4 	No
libz 	Yes
CharConv 	No
Protocols 	tftp, ftp, telnet, dict, ldap, ldaps, http, file, https, ftps
Host 	x86_64-pc-linux-gnu
SSL Version 	OpenSSL/0.9.8k
ZLib Version 	1.2.3.3 

3. Again, I am hiding these values for security reasons.

Thanks for you help BkkBonanza. Please read above, I indicated that the code has worked in the past and that I had to run sudo dpkg-reconfigure php5 whenever it did not work. But, for the past week its not successful.

Thanks again.

---

### Post by BkkBonanza on 2012-07-31
Is the subdirectory "app" still present and does it contain Mage.php? They also need to be readable by the user running the script.

I would uncomment a few of the debug lines in that file and see what it spits out. Those are lines starting with ////echo. Just remove the //// so the echo can work and it should give some status info while it runs.

Especially the line with 

////echo $res; 

and the one further down with 

////print_r($mageproducts);

See if the connection is being made and what data is being returned.

Curl seems to be present. And recent versions of PHP have DOM XML by default. Curl is pretty straightforward generally. So if that $res value returned by the curl call is not good then it would be something preventing it getting data.

---

### Post by cocotu on 2012-07-31
Thanks BkkBonanza!
I will post an update later today..thanks again.

---

### Post by cocotu on 2012-08-01
In this new Ubuntu server I get the output:
> 
[885631273562] => Array
        (
            [sku] => CE538A#BGJ
            [qty] => 0
            [upstatus] => 0
        )

    [884962455142] => Array
        (
            [sku] => CE841A#BGJ
            [qty] => 0
            [upstatus] => 0
        )

    [885631717066] => Array
        (
            [sku] => XN374A8#ABA
            [qty] => 0
            [upstatus] => 0
        )

)
<table border=1><tr><td>Sl.No</td><td>SKU</td><td>UPC#</td><td>Current Stock Status</td><td>Magento Stock</td><td>TechDat
a Stock</td><td>Cost</td><td>Magento Price</td><td>TechData Price</td></tr>

And nothing is updated. On the older(CentOS) server it works. How can I compare server configurations? Any ideas? Thanks again!

---

### Post by BkkBonanza on 2012-08-02
You are getting data now. It shows it above. But if you look at the last bit of code it only outputs the records in the table if the "upstatus" value is 1. But your data all has upstatus = 0. So the reason it's not showing is the data you are getting.

This line,

if($mageproducts[$productid]['upstatus']==1)
	{
...

stops any data from showing.

---

### Post by cocotu on 2012-08-03
If this is the case, why does it work at the old server?
I will investigate more. Thanks for helping!

---

### Post by spjackson on 2012-08-03
> **BkkBonanza said:**
> You are getting data now. It shows it above. But if you look at the last bit of code it only outputs the records in the table if the "upstatus" value is 1. But your data all has upstatus = 0. So the reason it's not showing is the data you are getting.

This line,

if($mageproducts[$productid]['upstatus']==1)
	{
...

stops any data from showing.

upstatus does not appear to come from the XML stream. It is metadata used by the script. It is initialised to 0 on line 33, then conditionally set to 1 on line 100.

It might be worth printing out $errorinfo, i.e.
```

		if($errorinfo->length==0)
			$mageproducts[$refid4->nodeValue]['upstatus']=1;
                else
                        print $errorinfo, "\n";

```

---

### Post by cocotu on 2012-08-04
I will give you the print out of $errorinfo as soon as i can.
Thanks for helping!

---

### Post by cocotu on 2012-08-06
Below is the output (partial):

> <br>init request<br>completed<pre><br>total 0<pre>Array
(
    [719192184275] => Array
        (
            [sku] => L2000CP-BF
            [qty] => 0
            [upstatus] => 0
        )

    [883609805180] => Array
        (
            [sku] => 4434HE1
            [qty] => 0
            [upstatus] => 0
        )

    [805736023909] => Array
        (
            [sku] => EA221WM-BK
            [qty] => 0
            [upstatus] => 0
.
.
.(more items-same as above)
.
<table border=1><tr><td>Sl.No</td><td>SKU</td><td>UPC#</td><td>Current Stock Status</td><td>Magento Stock</td><td>TechData Stock</td><td>Cost</td><td>Magent
o Price</td><td>TechData Price</td></tr>

Thanks for helping out!

---

### Post by BkkBonanza on 2012-08-06
It's not too clear from that what the errorinfo output is. Looking at the code I believe it's in the line before the product array. From what I can see it should be printing an errorinfo for each product item but that doesn't appear to be happening.

I'd suggest to debug further you'd want to add more "markers" in the output so you can see what code is being run or skipped over and how many times. By markers I mean just extra text labels like "ERR:", "HERE" etc.

---

### Post by cocotu on 2012-08-07
thanks for the tip!
i am very new to coding, how do i place "markers"in this case and where?

thanks again for helping!

---


---
title: "Php-fpm 7.4 and curl"
date: 2021-03-16
forum: Server Platforms
---

### Post by costel29 on 2021-03-16
Hi all,
please guide me to solve a problem that I can't find a solution to.
I have a server that runs several versions of PHP-FPM: 5.6, 7.4 and 8.0.
I have this code for get html order.

[PHP]
$order_details_link = base_url()."cart/order_details/".md5($order_id."key");
$curl = curl_init();		curl_setopt($curl, CURLOPT_URL, $order_details_link);		curl_setopt($curl, CURLOPT_FAILONERROR, true);		curl_setopt($curl, CURLOPT_FOLLOWLOCATION, true);		curl_setopt($curl, CURLOPT_RETURNTRANSFER, true);		$order_content = curl_exec($curl);		curl_close($curl);[/PHP]
CURL dont work if get link from variable.
if i print $order_details_link and use with this code work fine.
PHP]
$order_details_link = base_url()."cart/order_details/".md5($order_id."key");
$curl = curl_init();
		curl_setopt($curl, CURLOPT_URL, "https:/mydomain.com/cart/order_details/58d9b1b82256ba6bb4576cc387309237");
		curl_setopt($curl, CURLOPT_FAILONERROR, true);
		curl_setopt($curl, CURLOPT_FOLLOWLOCATION, true);
		curl_setopt($curl, CURLOPT_RETURNTRANSFER, true);
		$order_content = curl_exec($curl);
		curl_close($curl);
[/PHP]
Does anyone have any idea where the problem is?
CURL does not return any error messages except that the $ order_content variable remains empty
Thank you verry much

---

### Post by waffen on 2021-03-16
Looks like here is not the correct forum channel, did you check the logs? 
Add print statements to all your vars so you can see what's happening in each line.
I cant see any obvious issue in your code, so maybe is a logic bug

---

### Post by howefield on 2021-03-16
Thread moved to the "*Server Platforms*" forum for the time being.

---

### Post by costel29 on 2021-03-17
Hello,
sorry for wrong post channel.
I checked logs but dont write error in logs.
Also i checked [COLOR=#000000][FONT=Verdana]var_dump($order_details_link) and this result its empty.[/FONT][/COLOR]

---

### Post by waffen on 2021-03-17
> **costel29 said:**
> Hello,
sorry for wrong post channel.
I checked logs but dont write error in logs.
Also i checked [COLOR=#000000][FONT=Verdana]var_dump($order_details_link) and this result its empty.[/FONT][/COLOR]

Uhmm.. test each var inside it, if no error the problem is outside of that line.

---

### Post by costel29 on 2021-03-19
This script work fine on more servers.

---


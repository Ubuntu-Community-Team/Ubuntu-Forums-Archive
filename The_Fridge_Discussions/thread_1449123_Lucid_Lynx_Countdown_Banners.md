---
title: "Lucid Lynx Countdown Banners"
date: 2010-04-07
forum: The Fridge Discussions
---

### Post by TheFridge on 2010-04-07
The countdown banner is alive and counting down the days until 10.04 LTS is released.

Lets help build some excitement by spreading the word! We&#8217;ll need your help to tell others about the banner. Start by adding one of the three options to your website, the instructions are at [http://www.ubuntu.com/getubuntu/countdown](http://www.ubuntu.com/getubuntu/countdown)

We&#8217;d like to thank the artists who created this years chosen entries:

   * John Baer for the &#8220;change&#8221; artwork
   * Immanuel Peratoner for the &#8220;orange&#8221; artwork
   * Amanda Warzecha for the &#8220;lynx&#8221; artwork

Congratulations for the great work!

*Originally sent to the [ubuntu-news-team mailing list]("https://lists.ubuntu.com/archives/ubuntu-news-team/2010-April/000931.html") by Matthew Nuzum on Wed Apr 7 17:33:49 BST 2010*



[More...](http://fridge.ubuntu.com/node/2011)

---

### Post by paglia96 on 2010-04-07
I love the first  Immanuel Peratoner's countdown, that purple

---

### Post by Strongman332 on 2010-04-07
now all we need is something for facebook:popcorn:

---

### Post by l.billon on 2010-04-07
Yeah!
I was waiting for those since April 1st!
Putting one on my blog right now!

Big thanks to the artwork team!

---

### Post by Umang on 2010-04-08
Would it be possible to set up an image that is updated with a cron job so that those who cannot use JS will be able to have the image change as well?

---

### Post by l.billon on 2010-04-08
Hi!
I do not know if such a thing exists, 
However, this image is changed daily:
[http://countdown.immanuel-peratoner.de/index.php](http://countdown.immanuel-peratoner.de/index.php)

It is the one I use, for my website is non-JS.

---

### Post by Umang on 2010-04-08
Thanks. Hopefully the official set of images will have this ability next time. :)

---

### Post by bilalakhtar on 2010-04-09
People, the "Change" code is faulty.
For some reason, its displaying the 9.10 "Its here" image.
Please try to correct this :(:confused::popcorn::lolflag::guitar::lolflag:

---

### Post by itshorty on 2010-04-09
Like last release, I have created a PHP Script which delivers the right image.
It handles all 3 official Banners.

[http://neogates.ath.cx/~huwa/ubuntuLucid/](http://neogates.ath.cx/~huwa/ubuntuLucid/)

[IMG]http://neogates.ath.cx/~huwa/ubuntuLucid/lucid.php?id=1[/IMG][IMG]http://neogates.ath.cx/~huwa/ubuntuLucid/lucid.php?id=2[/IMG][IMG]http://neogates.ath.cx/~huwa/ubuntuLucid/lucid.php?id=3[/IMG]

mfg Florian Huber

---

### Post by rhkok on 2010-04-09
Has Sue Barr, the photographer of the Canadian Lynx in 'The Lynx', been contacted about using her photographic work in this artwork? Or has she released the picture under a free license?

[http://www.catsurvivaltrust.org/canlynxnf.htm](http://www.catsurvivaltrust.org/canlynxnf.htm)

Not to be a bugger, but I think copyrights should be respected.

Thx :)

Roeland

---

### Post by itshorty on 2010-04-09
> **Strongman332 said:**
> now all we need is something for facebook:popcorn:

I have done a small Facebook App to add a the banner to your Profile :)

[http://apps.facebook.com/ubuntubanner/](http://apps.facebook.com/ubuntubanner/)

---

### Post by Rmantingh on 2010-04-10
What happened to your Facebook app?
I had it up yesterday. Today it's no longer available!

---

### Post by Umang on 2010-04-10
> **rhkok said:**
> Has Sue Barr, the photographer of the Canadian Lynx in 'The Lynx', been contacted about using her photographic work in this artwork? Or has she released the picture under a free license?

[http://www.catsurvivaltrust.org/canlynxnf.htm](http://www.catsurvivaltrust.org/canlynxnf.htm)

Not to be a bugger, but I think copyrights should be respected.

Thx :)

Roeland
The images were made my Amanda Warzecha. Can't find any Launchpad user with that name, so I don't know how you would contact her to check.

---

### Post by itshorty on 2010-04-10
Sorry about that, but Facebook caches all images, so it wouldn't countdown :( 
I have tried several things like a JS which sets the right image URL, but it didn't work.

If there is anyone who has more expirience with the Facebook API (this was my fist contact with it), I would be glad to serve the whole thing. 

Here is the my code which doesen't work:

[PHP]
<?php
// Copyright 2007 Facebook Corp.  All Rights Reserved. 
// 
// Application: Ubuntu Banner
// File: 'index.php' 
//   This is a sample skeleton for your application. 
// 

require_once 'facebook.php';

$appapikey = '44df87f7559f57d342b8e50eddcb2655';
$appsecret = '53078f2bc7b2c786170668bd90d25111';
$facebook = new Facebook($appapikey, $appsecret);
$user_id = $facebook->require_login();

$id=0;
	if(isset($_GET['id'])){
		if ($_GET['id']>0&&$_GET['id']<=3){
			$id = $_GET['id'];
		}
$facebook->api_client->profile_setFBML(NULL, $user_id, 'profile', NULL, NULL, '<a href="http://www.ubuntu.com"><img id="ubuntuImg" src="http://neogates.ath.cx/~huwa/ubuntuLucid/lucid.php?id='.$id.'" alt="Ubuntu 10.4 Countdown"></a><script>document.images.ubuntuImg.src=http://neogates.ath.cx/~huwa/ubuntuLucid/lucid.php?id='.$id.'</script>');

	}



?>
<center>
<font color=red>Don't forget: <fb:add-section-button section="profile" /> (If you can't see a button, you allready added the banner to your profile)</font>
<p><center>Offical JavaScript Banners: <a href="http://www.ubuntu.com/getubuntu/countdown" >http://www.ubuntu.com/getubuntu/countdown</a><br>
Dynamic Serverside Banners: <a href="http://neogates.ath.cx/~huwa/ubuntuLucid"  >http://neogates.ath.cx/~huwa/ubuntuLucid</a><br>
</center></p>
<h2>Select Banner: </h2>
<table>
<tr>
<td>Option 1 - Change<br>by John Baer</td>
<td><a href="http://www.ubuntu.com"><img src="http://neogates.ath.cx/~huwa/ubuntuLucid/lucid.php?id=1" id="countdownimage" alt="Ubuntu 10.4 Countdown"></a></td>
<td><?php if ($id==1) { ?> Selected <?php } else { ?> <a href="?id=1">Select</a> <?php } ?></td>
<tr>
<td>Option 1 - Orange<br>by Immanuel Peratoner</td>
<td><a href="http://www.ubuntu.com"><img src="http://neogates.ath.cx/~huwa/ubuntuLucid/lucid.php?id=2" id="countdownimage" alt="Ubuntu 10.4 Countdown"></a></td>

<td><?php if ($id==2) { ?> Selected <?php } else { ?> <a href="?id=2">Select</a> <?php } ?></td>
<tr>
<td>Option 3 - lynx<br>by Amanda Warzecha</td>
<td><a href="http://www.ubuntu.com"><img src="http://neogates.ath.cx/~huwa/ubuntuLucid/lucid.php?id=3" id="countdownimage" alt="Ubuntu 10.4 Countdown"></a></td>
<td><?php if ($id==3) { ?> Selected <?php } else { ?> <a href="?id=3">Select</a> <?php } ?></td>

</table>
<font color=red>Don't forget: <fb:add-section-button section="profile" /> (If you can't see a button, you allready added the banner to your profile)</font>
<center>
More Info: <a href="https://wiki.ubuntu.com/Website/LucidCountdownBanners" >https://wiki.ubuntu.com/Website/LucidCountdownBanners</a>

[/PHP]

---

### Post by itshorty on 2010-04-10
btw... the API- and Secretkey is invalid :)

---


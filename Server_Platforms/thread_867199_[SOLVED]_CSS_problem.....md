---
title: "[SOLVED] CSS problem...."
date: 2008-07-22
forum: Server Platforms
---

### Post by bsharp on 2008-07-22
I've been tasked with designing a new website for church, and I'm having this bizarre (to me at least) problem where I'm losing a background color. Here's what I have (cleaned up as much as possible):             [php]<div class="content">
  <img style="width: 600px; height: 150px;" alt="Gas Banner" src="images/header_banner.jpg" /><br />
  <div class="navbar">
	<a class="navbar" href="#about.php">About Us</a> | 
	<a class="navbar" href="#calendar.php">Calendar</a> |
	<a class="navbar" href="#directions.php">Directions</a> | 
	<a class="navbar" href="#media.php">Media</a> | 
	<a class="navbar" href="#attendants.php">The Attendants</a>
  </div>
  <div class="news">
	<?php 
          $amount=1;
          get_news($cxn,@$date,$amount,@$type);
	?>
  </div>
  <div class="preview">
	<?php
          $type='preview';
	  $amount=5;
          get_news($cxn,@$date,$amount,$type);
	?>
  </div>
  <div class="footer" style="text-align: left; float: left;">
  Copyright © 2008 The GAS Station
  </div>
  <div class="footer" style="text-align: right; float: right;">
    <a href="#admin.php" id="footer">Admin Login</a>
  </div>
</div>[/php]                                                             And here's the relevant stylesheet info:                                  [php].content {
  	font-family: Verdana,Arial,Helvetica,sans-serif;
  	font-size: small;
  	color: #474747;
  	text-decoration: none;
  	border-right-style: groove;
  	border-left-style: ridge;
  	background-color: #FFFFFF;
  	margin-left: auto;
  	margin-right: auto;
  	border-right-width: 5px;
	border-left-width: 5px;
  	width: 750px;
}
.navbar {
  	background-color: black;
}
.news {
	background-color: white;
  	text-align: left;
  	width: 595px;
  	min-width: 595px;
  	max-width: 595px;
  	margin-left: 5px;
  	margin-right: 5px;
  	margin-top: 5px;
  	border-style: solid;
  	border-width: 1px;
  	border-color: #BABABA;
  	float: left;
}
.preview {
	background-color: white;
	color: $4b4b4b;
	text-align: left;
	width: 130px;
	margin-top: 5px;
	margin-left: 5px;
	border-style: solid;
  	border-width: 1px;
  	border-color: #BABABA;
  	float: left;
}
.footer {
  	background-color: #848484;
  	text-decoration: none;
  	font-family: Verdana,Arial,Helvetica,sans-serif;
  	font-size: small;
  	width: 375px;
  	margin-left: auto;
	margin-right: auto;
}[/php]                                                                    The background color for .content refuses to show up, even though .news and .preview are within the <div>. When I take float: left off of either .preview and .news (doesn't matter which), the white magically appears, but my alignment is off. I pretty much started learning CSS this morning, so it's probably something stupid. Does anyone have any ideas or am I going to have to resort to frames?                                        Sorry for the long post and thanks for any help. :KS

---

### Post by bsharp on 2008-07-22
Got it! Added position: absolute; with an offset of left: 25%; to .content, marking as solved.

---


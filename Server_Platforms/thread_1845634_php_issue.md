---
title: "php issue"
date: 2011-09-17
forum: Server Platforms
---

### Post by silameth on 2011-09-17
I have an issue with a .php page, others in the same directory as well as other directories work fine. It just won't show anything but white page. I think I have narrowed it down to a "pebkac" error.
I just can't see it. Any help would be appreciated.
I double checked the css it is all correct.
here is the source for my index.php that is being a pain.
[HTML]<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 
<html lang="en" xmlns="http://www.w3.org/1999/xhtml"> 
<head> 
<title>ourhelpgroup.com |</title> 
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
<meta name="description" content="description"/> 
<meta name="keywords" content="keywords"/>  
<meta name="author" content="root" />  
<link href="style.css" rel="stylesheet" type="text/css" /> 
</head> 
<body> 
<div id="container"> 
  <div id="top"> 
    <h1><span style="color: #A662AA;">Our</span> Help<span style="color: #A662AA;">Group</span></h1> 
     
  </div> 
  <div id="navcontainer"> 
    <? include ('nav.php'); ?> 
  </div> 
  <div id="leftnav"> 
    <h2>More Links</h2> 
    <? include ('morelinks.php'); /?> 
    <h2>Archives</h2> 
   <? include ('archive.php'); /?> 
    <p class="quote"></p> 
  </div> 
  <div id="content"> 
    <h2>Welcome to <span style="font-weight:bold; color:#A662AA;">Our</span>Help<span style="font-weight:bold; color:#A662AA;">Group</Span></h2> 
    <blockquote><img class="imgleft" src="images/badge.png" alt="" />Helping others is what we do.</blockquote> 
    <p></p> 
    <p></p> 
    <h2>Sub content</h2> 
    <p></p> 
  </div> 
  <div id="columns"> 
    <div class="col3"> 
      <h2>Updates</h2> 
      <div class="navlist"> 
        <? include ('updates.php'); /?> 
      </div> 
    </div> 
    <div class="col3center"> 
      <h2>Resources</h2> 
      <div class="navlist"> 
        <? include ('resources.php'); /?> 
      </div> 
    </div> 
    <div class="col3"> 
      <h2>Links</h2> 
      <div class="navlist"> 
        <? include ('links.php'); /?> 
      </div> 
    </div> 
  </div> 
  <div id="footer"> 
    <? include_once('footer.php'); /?> 
  </div> 
</div> 
</body> 
</html> 
[/HTML]

---

### Post by silameth on 2011-09-17
Never mind, I found it.... it was simple.
it was the /?>, I took out the / and it works fine. 

I am going to call it solved and leave it for anyothers to laugh at.

---


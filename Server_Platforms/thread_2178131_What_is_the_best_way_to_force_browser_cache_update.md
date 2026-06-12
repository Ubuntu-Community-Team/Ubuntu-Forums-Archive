---
title: "What is the best way to force browser cache update?"
date: 2013-10-02
forum: Server Platforms
---

### Post by coldraven on 2013-10-02
Sorry but I did a lot of searching and did not really understand the answers that I found.
I recently did a lot of updates on a site that I maintain but found that no-one was seeing the new pages.
Of course I know to press F5 to update the browser's cache but the general public do not.
The site was created a long time ago and could probably be completely re-written or a CMS installed. Suggestions welcome.
My index.htm looks like this.
```
<html> 
<head> 
<title>Longhope Lifeboat Museum Trust</title> 
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1"> 
</head> 
<frameset rows="75,460*" cols="100,*" frameborder="NO" border="0" framespacing="0">  
  <frame name="cornerFrame" scrolling="NO" noresize src="logo1.htm" marginwidth="0" marginheight="0" > 
  <frame name="topFrame" src="top.htm" marginwidth="0" marginheight="0" noresize scrolling="AUTO" > 
  <frame name="leftFrame" src="navvy1.htm"> 
  <frame name="mainFrame" src="home.htm"> 
</frameset> 
<noframes>  
<body bgcolor="#FFFFFF"> 
</body> 
</noframes>  
</html>
```
As you can see it just loads pages into frames, so I guess that I would have to put "no-cache" into almost every page on the site.
If I was using Drupal or Joomla (or some other CMS) is it possible to force an update of the entire site with just one edit?
Thanks for any advice.

---

### Post by SeijiSensei on 2013-10-04
You can add

```

<meta http-equiv='cache-control' content='no-cache'>
<meta http-equiv='expires' content='-1'>

```

to the [noparse]<head></head>[/noparse] section of the page.  Together those will force the browser not to cache the content.  

Since these are really HTTP commands, you can alternatively place [directives]("http://www.mat-wright.com/2010/02/apache-cache-control.html") in Apache to deny caching.  This method will apply to all content downloaded from the site, not just the page in question.  Choose one or the other method depending on your needs.

---


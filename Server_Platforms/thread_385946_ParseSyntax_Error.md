---
title: "Parse/Syntax Error:"
date: 2007-03-16
forum: Server Platforms
---

### Post by uamusa on 2007-03-16
When navigating to a particular php page, I get the following error:

"Parse error: syntax error, unexpected** ';', **expecting** ')' **in /home/chris/public_html/accessmonticello.com/classifieds/conf_cat.php **on line 170**"


**Below I have included the last few lines in that file:**

166  'height'=>'yes', 'comment'=>'yes'),
167
168  # Table bgcolor for layers of highlighted ad
169  $tbclhlads="#aa5555",
170
171  ?>
172


So, I just know the answer is so blatantly obvious that I'm going to feel really stupid, but I'm just not seeing it this morning.

Thanks --Chris

---

### Post by uamusa on 2007-03-16
I figured it out......in fact I had actually left out a ";" way back on line 120.....but but the error wasn't realized until near the end of the file.

---


---
title: "Looking for CSS gurus"
date: 2012-05-10
forum: The Cafe
---

### Post by Technoviking on 2012-05-10
I'm working on a new theme for forums to match the main Ubuntu site and could use some CSS advice. Please let me know if you can help.

Thanks,
T-V

---

### Post by CharlesA on 2012-05-10
*waves*

I don't much all that much about CSS, but what do you need help with?

---

### Post by bodhi.zazen on 2012-05-10
There are several staff members versed in the dark art of css.

Take a look at this:

[http://userstyles.org/styles/40915/ubuntu-forums-new-theme](http://userstyles.org/styles/40915/ubuntu-forums-new-theme)

Click the "Show Code" button ;)

---

### Post by codingman on 2012-05-10
Cheese! that's a lot of css!

one thing: use the new ubuntu logo, and keep out the brown!

try to make things be a box, like make a background color and then make it a block type, the forum now has too many basic "links" that look dull and boring. Try not to use deprecated tags, only css and well id's,names and classes.

---

### Post by codingman on 2012-05-10
Oh, and try to not to put any text-decorations for links, it looks better without an underline, you can do this by doing:
```

a {text-decoration:none;}

```
use psuedo classes too! They make cool websites! like :hover and :active check here for an example i made:

[http://www.armeencode.com](http://www.armeencode.com)

Hope this helps!
codingman

---

### Post by CharlesA on 2012-05-10
> **codingman said:**
> Oh, and try to not to put any text-decorations for links, it looks better without an underline, you can do this by doing:
```

a {text-decoration:none;}

```
use psuedo classes too! They make cool websites! like :hover and :active check here for an example i made:

[http://www.armeencode.com](http://www.armeencode.com)

Hope this helps!
codingman
Keep in mind that if the link is the same color as the text, it will be hard to tell if it is a link or not.

Underline ftw

---

### Post by Technoviking on 2012-05-10
The new style is Ubuntu New. The navbar, New Reply and forum titles are giving us headaches.

T-V

---

### Post by bodhi.zazen on 2012-05-10
> **Technoviking said:**
> The new style is Ubuntu New. The navbar, New Reply and forum titles are giving us headaches.

T-V

Can you post the css for those items ? Makes it easier to review.

---

### Post by Technoviking on 2012-05-10
```
.vblcean_msgpost{display:block}
.vblcean_msgpost *{
  display:block;
  height:1px;
  overflow:hidden;
  font-size:.01em;
  background:#f8f8f3}
.vblcean_msgpost1{
  margin-left:3px;
  margin-right:3px;
  padding-left:1px;
  padding-right:1px;
  border-left:1px solid #fbfbf9;
  border-right:1px solid #fbfbf9;
  background:#f9f9f6}
.vblcean_msgpost2{
  margin-left:1px;
  margin-right:1px;
  padding-right:1px;
  padding-left:1px;
  border-left:1px solid #fefefd;
  border-right:1px solid #fefefd;
  background:#f9f9f5}
.vblcean_msgpost3{
  margin-left:1px;
  margin-right:1px;
  border-left:1px solid #f9f9f5;
  border-right:1px solid #f9f9f5;}
.vblcean_msgpost4{
  border-left:1px solid #fbfbf9;
  border-right:1px solid #fbfbf9}
.vblcean_msgpost5{
  border-left:1px solid #f9f9f6;
  border-right:1px solid #f9f9f6}
.vblcean_msgpostfg{
  background:#f8f8f3; padding: 3px;}

.vbclean_postbit_header{display:block}
.vbclean_postbit_header *{
  display:block;
  height:1px;
  overflow:hidden;
  font-size:.01em;
  background:#E4ECF5}
.vbclean_postbit_header1{
  margin-left:3px;
  margin-right:3px;
  padding-left:1px;
  padding-right:1px;
  border-left:1px solid #eff2f3;
  border-right:1px solid #eff2f3;
  background:#e9eff4}
.vbclean_postbit_header2{
  margin-left:1px;
  margin-right:1px;
  padding-right:1px;
  padding-left:1px;
  border-left:1px solid #f6f6f3;
  border-right:1px solid #f6f6f3;
  background:#e7eef4}
.vbclean_postbit_header3{
  margin-left:1px;
  margin-right:1px;
  border-left:1px solid #e7eef4;
  border-right:1px solid #e7eef4;}
.vbclean_postbit_header4{
  border-left:1px solid #eff2f3;
  border-right:1px solid #eff2f3}
.vbclean_postbit_header5{
  border-left:1px solid #e9eff4;
  border-right:1px solid #e9eff4}
.vbclean_postbit_headerfg{
  background:#E4ECF5; padding: 3px;}



.vbclean_bottom{display:block; width: 99%}
.vbclean_bottom *{
  display:block;
  height:1px;
  overflow:hidden;
  font-size:.01em;
  background:#FFFFFF}
.vbclean_bottom1{
  margin-left:3px;
  margin-right:3px;
  padding-left:1px;
  padding-right:1px;
  border-left:1px solid #eff4f9;
  border-right:1px solid #eff4f9;
  background:#f8fafc}
.vbclean_bottom2{
  margin-left:1px;
  margin-right:1px;
  padding-right:1px;
  padding-left:1px;
  border-left:1px solid #e6edf6;
  border-right:1px solid #e6edf6;
  background:#f9fbfd}
.vbclean_bottom3{
  margin-left:1px;
  margin-right:1px;
  border-left:1px solid #f9fbfd;
  border-right:1px solid #f9fbfd;}
.vbclean_bottom4{
  border-left:1px solid #eff4f9;
  border-right:1px solid #eff4f9}
.vbclean_bottom5{
  border-left:1px solid #f8fafc;
  border-right:1px solid #f8fafc}
.vbclean_bottomfg{
  background:#FFFFFF}

.vblcean_navbar{
  display:block;
  }
.vblcean_navbar *{
  display:block;
  height:1px;
  overflow:hidden;
  font-size:.01em}
.vblcean_navbarfg a{ 
 color: #ffffff}
.vblcean_navbar1{
  margin-left:3px;
  margin-right:3px;
  padding-left:1px;
  padding-right:1px;
  border-left:1px solid #f5f5ef;
  border-right:1px solid #f5f5ef;
  background:#dd4814}
.vblcean_navbar2{
  margin-left:1px;
  margin-right:1px;
  padding-right:1px;
  padding-left:1px;
  border-left:1px solid #fcfcfb;
  border-right:1px solid #fcfcfb;
  background:#dd4814}
.vblcean_navbar3{
  margin-left:1px;
  margin-right:1px;
  border-left:1px solid #edede1;
  border-right:1px solid #edede1;
  background:#dd4814}
.vblcean_navbar4{
  border-left:1px solid #f5f5ef;
  border-right:1px solid #f5f5ef
  background:#dd4814}
.vblcean_navbar5{
  border-left:1px solid #efefe3;
  border-right:1px solid #efefe3
  background:#dd4814}
.vblcean_navbarfg{
  background:#dd4814}



.vbclean_lastpost{display:block}
.vbclean_lastpost *{
  display:block;
  height:1px;
  overflow:hidden;
  font-size:.01em;
  background:#EEEEEE}
.vbclean_lastpost1{
  margin-left:3px;
  margin-right:3px;
  padding-left:1px;
  padding-right:1px;
  border-left:1px solid #f7f7f7;
  border-right:1px solid #f7f7f7;
  background:#f2f2f2}
.vbclean_lastpost2{
  margin-left:1px;
  margin-right:1px;
  padding-right:1px;
  padding-left:1px;
  border-left:1px solid #fdfdfd;
  border-right:1px solid #fdfdfd;
  background:#f1f1f1}
.vbclean_lastpost3{
  margin-left:1px;
  margin-right:1px;
  border-left:1px solid #f1f1f1;
  border-right:1px solid #f1f1f1;}
.vbclean_lastpost4{
  border-left:1px solid #f7f7f7;
  border-right:1px solid #f7f7f7}
.vbclean_lastpost5{
  border-left:1px solid #f2f2f2;
  border-right:1px solid #f2f2f2}
.vbclean_lastpostfg{
  background:#EEEEEE; padding: 5px;}

.vbclean_msgpost
{
	color: #B02B2C;
	font: bold 14px Ubuntu, Arial, Sans-Serif;
	letter-spacing: -1px;
}
.vbclean_msgpost a:link, .vbclean_msgpost_alink
{
	color: #B02B2C;
	text-decoration: bold;
}
.vbclean_msgpost a:visited, .vbclean_msgpost_avisited
{
	color: #B02B2C;
	text-decoration: bold;
}
.vbclean_msgpost a:hover, .vbclean_msgpost a:active, .vbclean_msgpost_ahover
{
	color: #222;
	text-decoration: underline;
}

.vbclean_msgpost_bit
{
	color: #B02B2C;
	font: bold 12px Ubuntu, Arial, Sans-Serif;
	letter-spacing: -1px;
}
.vbclean_msgpost_bit a:link, .vbclean_msgpost_bit_alink
{
	color: #B02B2C;
	text-decoration: bold;
}
.vbclean_msgpost_bit a:visited, .vbclean_msgpost_bit_avisited
{
	color: #B02B2C;
	text-decoration: bold;
}
.vbclean_msgpost_bit a:hover, .vbclean_msgpost_bit a:active, .vbclean_msgpost_bit_ahover
{
	color: #222;
	text-decoration: underline;
}

.vbclean_navbar
{
	background: #eeeeee;
	color: #FFFFFF;
	font: bold 12px Ubuntu, Arial, Sans-Serif;
	padding: 3px 6px 3px 6px;
	white-space: nowrap;
	
}
.vbclean_navbar a:link, .vbclean_navbar_alink
{
	color: #356AA0;
	text-decoration: underline;
}
.vbclean_navbar a:visited, .vbclean_navbar_avisited
{
	color: #356AA0;
	text-decoration: underline;
}
.vbclean_navbar a:hover, .vbclean_navbar a:active, .vbclean_navbar_ahover
{
	color: #FFFFFF;
	text-decoration: underline;
}
.vbclean_prefix 
{
	color: #333;
	font: normal 11px Ubuntu, Arial, Sans-Serif;
}
.vbclean_navbar_bg
{
	background: #dd4814;
	color: #333;
	font: bold 12px Ubuntu, Arial, Sans-Serif;
	padding: 3px 6px 3px 6px;
	white-space: nowrap;
	
}
.vbclean_navbar_bg a:link, .vbclean_navbar_bg_alink
{
	color: #333;
	text-decoration: none;
}
.vbclean_navbar_bg a:visited, .vbclean_navbar_bg_avisited
{
	color: #333;
	text-decoration: none;
}
.vbclean_navbar_bg a:hover, .vbclean_navbar_bg a:active, .vbclean_navbar_bg_ahover
{
	color: #FFFFFF;
	text-decoration: underline;
}
.smallfont_foruminfo
{
	color: #333;
	font: bold 10px Ubuntu, Arial, Sans-Serif;
	padding: 3px 6px 3px 6px;
	white-space: nowrap;
	
}
.forum_fpinfo{display:block}
.forum_fpinfo *{
  display:block;
  height:1px;
  overflow:hidden;
  font-size:.01em;
  background:#EEEEEE}
.forum_fpinfo1{
  margin-left:3px;
  margin-right:3px;
  padding-left:1px;
  padding-right:1px;
  border-left:1px solid #f7f7f7;
  border-right:1px solid #f7f7f7;
  background:#f2f2f2}
.forum_fpinfo2{
  margin-left:1px;
  margin-right:1px;
  padding-right:1px;
  padding-left:1px;
  border-left:1px solid #fdfdfd;
  border-right:1px solid #fdfdfd;
  background:#f1f1f1}
.forum_fpinfo3{
  margin-left:1px;
  margin-right:1px;
  border-left:1px solid #f1f1f1;
  border-right:1px solid #f1f1f1;}
.forum_fpinfo4{
  border-left:1px solid #f7f7f7;
  border-right:1px solid #f7f7f7}
.forum_fpinfo5{
  border-left:1px solid #f2f2f2;
  border-right:1px solid #f2f2f2}
.forum_fpinfofg{
  background:#EEEEEE}

.vbclean_forumhomecat
{
	color: #c00;
	font: bold 1.2em Ubuntu, Arial, Sans-Serif;
}

.vbclean_forumhomecat a:link, .vbclean_forumhomecat_alink
{
	color: #c00;
        text-decoration: none;
}
.vbclean_forumhomecat a:visited, .vbclean_forumhomecat_avisited
{
	color: #c00;
	text-decoration: none;
}
.vbclean_forumhomecat a:hover, .vbclean_forumhomecat a:active, .vbclean_forumhomecat_ahover
{
	color: #c00;
	text-decoration: none;
}


.vbclean_navbar{display:block}
.vbclean_navbar *{
  display:block;
  height:1px;
  overflow:hidden;
  font-size:.01em;
  background:#f7f7f7}
.vbclean_navbar1{
  margin-left:3px;
  margin-right:3px;
  padding-left:1px;
  padding-right:1px;
  border-left:1px solid #f5f5ef;
  border-right:1px solid #f5f5ef;
  background:#efefe3}
.vbclean_navbar2{
  margin-left:1px;
  margin-right:1px;
  padding-right:1px;
  padding-left:1px;
  border-left:1px solid #fcfcfb;
  border-right:1px solid #fcfcfb;
  background:#edede1}
.vbclean_navbar3{
  margin-left:1px;
  margin-right:1px;
  border-left:1px solid #edede1;
  border-right:1px solid #edede1;}
.vbclean_navbar4{
  border-left:1px solid #f5f5ef;
  border-right:1px solid #f5f5ef}
.vbclean_navbar5{
  border-left:1px solid #efefe3;
  border-right:1px solid #efefe3}
.vbclean_navbarfg{
  background:#f7f7f7}
.vbclean_welcomemsg{display:block}
.vbclean_welcomemsg *{
  display:block;
  height:1px;
  overflow:hidden;
  font-size:.01em;
  background:#F5F3DC}
.vbclean_welcomemsg1{
  margin-left:3px;
  margin-right:3px;
  padding-left:1px;
  padding-right:1px;
  border-left:1px solid #faf9ef;
  border-right:1px solid #faf9ef;
  background:#f7f6e4}
.vbclean_welcomemsg2{
  margin-left:1px;
  margin-right:1px;
  padding-right:1px;
  padding-left:1px;
  border-left:1px solid #fefdfb;
  border-right:1px solid #fefdfb;
  background:#f6f5e2}
.vbclean_welcomemsg3{
  margin-left:1px;
  margin-right:1px;
  border-left:1px solid #f6f5e2;
  border-right:1px solid #f6f5e2;}
.vbclean_welcomemsg4{
  border-left:1px solid #faf9ef;
  border-right:1px solid #faf9ef}
.vbclean_welcomemsg5{
  border-left:1px solid #f7f6e4;
  border-right:1px solid #f7f6e4}
.vbclean_welcomemsgfg{
  background:#F5F3DC;
padding:0 5px;}

.vbclean_sticky{display:block}
.vbclean_sticky *{
  display:block;
  height:1px;
  overflow:hidden;
  font-size:.01em;
  background:#f7f7f7}
.vbclean_sticky1{
  margin-left:3px;
  margin-right:3px;
  padding-left:1px;
  padding-right:1px;
  border-left:1px solid #f5f5ef;
  border-right:1px solid #f5f5ef;
  background:#efefe3}
.vbclean_sticky2{
  margin-left:1px;
  margin-right:1px;
  padding-right:1px;
  padding-left:1px;
  border-left:1px solid #fcfcfb;
  border-right:1px solid #fcfcfb;
  background:#edede1}
.vbclean_sticky3{
  margin-left:1px;
  margin-right:1px;
  border-left:1px solid #edede1;
  border-right:1px solid #edede1;}
.vbclean_sticky4{
  border-left:1px solid #f5f5ef;
  border-right:1px solid #f5f5ef}
.vbclean_sticky5{
  border-left:1px solid #efefe3;
  border-right:1px solid #efefe3}
.vbclean_stickyfg{
  background:#eaeada; padding: 0 5px;}

.vbclean_newthread{display:block; width: 130px;}
.vbclean_newthread *{
  display:block;
  height:1px;
  overflow:hidden;
  font-size:.01em;
  background:#DD4814}
.vbclean_newthread1{
  margin-left:3px;
  margin-right:3px;
  padding-left:1px;
  padding-right:1px;
  border-left:1px solid #d8d3c8;
  border-right:1px solid #d8d3c8;
  background:#bcb3a0}
.vbclean_newthread2{
  margin-left:1px;
  margin-right:1px;
  padding-right:1px;
  padding-left:1px;
  border-left:1px solid #f6f4f2;
  border-right:1px solid #f6f4f2;
  background:#b6ad98}
.vbclean_newthread3{
  margin-left:1px;
  margin-right:1px;
  border-left:1px solid #b6ad98;
  border-right:1px solid #b6ad98;}
.vbclean_newthread4{
  border-left:1px solid #d8d3c8;
  border-right:1px solid #d8d3c8}
.vbclean_newthread5{
  border-left:1px solid #bcb3a0;
  border-right:1px solid #bcb3a0}
.vbclean_newthreadfg{
  background:#DD4814;
  color: #FFFFFF;
  font: bold 13px Ubuntu, Arial, Sans-Serif;
  letter-spacing: -1px;
  width: 130px;
  }


.vbclean_newthreadfg a:link, .vbclean_newthreadfg_alink
{
	color: #FFFFFF;
	text-decoration: bold;
}
.vbclean_newthreadfg a:visited, .vbclean_newthreadfg_avisited
{
	color: #FFFFFF;
	text-decoration: bold;
}
.vbclean_newthreadfg a:hover, .vbclean_newthreadfg a:active, .vbclean_newthreadfg_ahover
{
	color: #FFFFFF;
	text-decoration: underline;
}

.vbclean_forumdesc{display:block}
.vbclean_forumdesc *{
  display:block;
  height:1px;
  overflow:hidden;
  font-size:.01em;
  background:#f7f7f7}
.vbclean_forumdesc1{
  margin-left:3px;
  margin-right:3px;
  padding-left:1px;
  padding-right:1px;
  border-left:1px solid #f5f5ef;
  border-right:1px solid #f5f5ef;
  background:#f7f7f7}
.vbclean_forumdesc2{
  margin-left:1px;
  margin-right:1px;
  padding-right:1px;
  padding-left:1px;
  border-left:1px solid #fcfcfb;
  border-right:1px solid #fcfcfb;
  background:#f7f7f7}
.vbclean_forumdesc3{
  margin-left:1px;
  margin-right:1px;
  border-left:1px solid #f7f7f7;
  border-right:1px solid #f7f7f7;}
.vbclean_forumdesc4{
  border-left:1px solid #f7f7f7;
  border-right:1px solid #f7f7f7}
.vbclean_forumdesc5{
  border-left:1px solid #f7f7f7;
  border-right:1px solid #f7f7f7}
.vbclean_forumdescfg{
  background:#f7f7f7}

.forumhome_stats {
font:normal 11px Ubuntu, Tahoma, Sans, Arial, Helvetica, sans-serif;
color:#656565;
font-weight:400;
}

.vbclean_fhomecat{display:block}
.vbclean_fhomecat *{
  display:block;
  height:1px;
  overflow:hidden;
  font-size:.01em;
  background:#f7f7f7}
.vbclean_fhomecat1{
  margin-left:3px;
  margin-right:3px;
  padding-left:1px;
  padding-right:1px;
  border-left:1px solid #fbfaf8;
  border-right:1px solid #fbfaf8;
  background:#f8f7f3}
.vbclean_fhomecat2{
  margin-left:1px;
  margin-right:1px;
  padding-right:1px;
  padding-left:1px;
  border-left:1px solid #fefefd;
  border-right:1px solid #fefefd;
  background:#f7f6f2}
.vbclean_fhomecat3{
  margin-left:1px;
  margin-right:1px;
  border-left:1px solid #f7f6f2;
  border-right:1px solid #f7f6f2;}
.vbclean_fhomecat4{
  border-left:1px solid #fbfaf8;
  border-right:1px solid #fbfaf8}
.vbclean_fhomecat5{
  border-left:1px solid #f8f7f3;
  border-right:1px solid #f8f7f3}
.vbclean_fhomecatfg{
  background:#f7f7f7; padding: 0 10px;}

.vbclean_fhomecat_top{display:block}
.vbclean_fhomecat_top *{
  display:block;
  height:1px;
  overflow:hidden;
  font-size:.01em;
  background:#F7f7f7}
.vbclean_fhomecat_top1{
  margin-left:3px;
  margin-right:3px;
  padding-left:1px;
  padding-right:1px;
  border-left:1px solid #f8f8ee;
  border-right:1px solid #f8f8ee;
  background:#f3f3e1}
.vbclean_fhomecat_top2{
  margin-left:1px;
  margin-right:1px;
  padding-right:1px;
  padding-left:1px;
  border-left:1px solid #fdfdfb;
  border-right:1px solid #fdfdfb;
  background:#f2f2df}
.vbclean_fhomecat_top3{
  margin-left:1px;
  margin-right:1px;
  border-left:1px solid #f2f2df;
  border-right:1px solid #f2f2df;}
.vbclean_fhomecat_top4{
  border-left:1px solid #f8f8ee;
  border-right:1px solid #f8f8ee}
.vbclean_fhomecat_top5{
  border-left:1px solid #f3f3e1;
  border-right:1px solid #f3f3e1}
.vbclean_fhomecat_topfg{
  background:#f7f7f7; padding: 0 5px;}


.vbclean_announce{display:block}
.vbclean_announce *{
  display:block;
  height:1px;
  overflow:hidden;
  font-size:.01em;
  background:#eae4e4}
.vbclean_announce1{
  margin-left:3px;
  margin-right:3px;
  padding-left:1px;
  padding-right:1px;
  border-left:1px solid #e5eeff;
  border-right:1px solid #e5eeff;
  background:#d2e2ff}
.vbclean_announce2{
  margin-left:1px;
  margin-right:1px;
  padding-right:1px;
  padding-left:1px;
  border-left:1px solid #f9fbff;
  border-right:1px solid #f9fbff;
  background:#cee0ff}
.vbclean_announce3{
  margin-left:1px;
  margin-right:1px;
  background:#eae4e4; 
  border-left:1px solid #eae4e4;
  border-right:1px solid #eae4e4}
.vbclean_announce4{
  background:#eae4e4; 
  border-left:1px solid #eeeeee;
  border-right:1px solid #eeeeee}
.vbclean_announce5{
  background:#eae4e4; 
  border-left:1px solid #eeeeee;
  border-right:1px solid #eeeeee}
.vbclean_announcefg{
  background:#eae4e4; padding: 0 5px}

.vbclean_top{display:block; width: 99%;}
.vbclean_top *{
  display:block;
  height:1px;
  overflow:hidden;
  font-size:.01em;
  background:#FFFFFF}
.vbclean_top1{
  margin-left:3px;
  margin-right:3px;
  padding-left:1px;
  padding-right:1px;
  border-left:1px solid #ffffff;
  border-right:1px solid #ffffff}
.vbclean_top2{
  margin-left:1px;
  margin-right:1px;
  padding-right:1px;
  padding-left:1px;
  border-left:1px solid #ffffff;
  border-right:1px solid #ffffff}
.vbclean_top3{
  margin-left:1px;
  margin-right:1px;
  border-left:1px solid #ffffff;
  border-right:1px solid #ffffff}
.vbclean_top4{
  border-left:1px solid #ffffff;
  border-right:1px solid #ffffff}
.vbclean_top5{
  border-left:1px solid #ffffff;
  border-right:1px solid #ffffff}
.vbclean_topfg{
  background:#FFFFFF;}

.ubuntu_quotebackground {
background:#F8F8F3;
border-right:1px solid #ddddc5;
border-top:1px solid #ddddc5;
border-left:6px solid #ddddc5;
border-bottom:1px solid #ddddc5;
}

.ubuntu_codebackground {
font-weight:700;
font:normal 1em Ubuntu, Arial, Sans-Serif;
background:#F8F8F3;
border-right:1px solid #ddddc5;
border-top:1px solid #ddddc5;
border-left:6px solid #ddddc5;
border-bottom:1px solid #ddddc5;
}


.vbclean_postbit{display:block}
.vbclean_postbit *{
  display:block;
  height:1px;
  overflow:hidden;
  font-size:.01em;
  background:##F8F8F3}
.vbclean_postbit1{
  margin-left:3px;
  margin-right:3px;
  padding-left:1px;
  padding-right:1px;
  border-left:1px solid #fbfbf9;
  border-right:1px solid #fbfbf9;
  background:#f9f9f6}
.vbclean_postbit2{
  margin-left:1px;
  margin-right:1px;
  padding-right:1px;
  padding-left:1px;
  border-left:1px solid #fefefd;
  border-right:1px solid #fefefd;
  background:#f9f9f5}
.vbclean_postbit3{
  margin-left:1px;
  margin-right:1px;
  border-left:1px solid #f9f9f5;
  border-right:1px solid #f9f9f5;}
.vbclean_postbit4{
  border-left:1px solid #fbfbf9;
  border-right:1px solid #fbfbf9}
.vbclean_postbit5{
  border-left:1px solid #f9f9f6;
  border-right:1px solid #f9f9f6}
.vbclean_postbitfg{
  background:##F8F8F3; padding: 0 5px;}

.alt3
{
	background: ##f7f7f7;
        border-right: 2px solid #DDDDDD;
}

.alt4
{
	background: #f7f7f7;
        border-bottom: 2px solid #dddddd;
}

.vbclean_postbitleg{display:block}
.vbclean_postbitleg *{
  display:block;
  height:1px;
  overflow:hidden;
  font-size:.01em;
  background:#f7f7f7}
.vbclean_postbitleg1{
  margin-left:3px;
  margin-right:3px;
  padding-left:1px;
  padding-right:1px;
  border-left:1px solid #f5f5ef;
  border-right:1px solid #f5f5ef;
  background:#efefe3}
.vbclean_postbitleg2{
  margin-left:1px;
  margin-right:1px;
  padding-right:1px;
  padding-left:1px;
  border-left:1px solid #fcfcfb;
  border-right:1px solid #fcfcfb;
  background:#edede1}
.vbclean_postbitleg3{
  margin-left:1px;
  margin-right:1px;
  border-left:1px solid #edede1;
  border-right:1px solid #edede1;}
.vbclean_postbitleg4{
  border-left:1px solid #f5f5ef;
  border-right:1px solid #f5f5ef}
.vbclean_postbitleg5{
  border-left:1px solid #efefe3;
  border-right:1px solid #efefe3}
.vbclean_postbitlegfg{
  background:#f7f7f7; padding: 0 5px;}


.vbclean_postbitmsg{display:block}
.vbclean_postbitmsg *{
  display:block;
  height:1px;
  overflow:hidden;
  font-size:.01em;
  background:#FFFFFf}
.vbclean_postbitmsg1{
  margin-left:3px;
  margin-right:3px;
  padding-left:1px;
  padding-right:1px;
  border-left:1px solid #f3f3e9;
  border-right:1px solid #f3f3e9;
  background:#f9f9f5}
.vbclean_postbitmsg2{
  margin-left:1px;
  margin-right:1px;
  padding-right:1px;
  padding-left:1px;
  border-left:1px solid #ececdd;
  border-right:1px solid #ececdd;
  background:#fbfbf7}
.vbclean_postbitmsg3{
  margin-left:1px;
  margin-right:1px;
  border-left:1px solid #fbfbf7;
  border-right:1px solid #fbfbf7;}
.vbclean_postbitmsg4{
  border-left:1px solid #f3f3e9;
  border-right:1px solid #f3f3e9}
.vbclean_postbitmsg5{
  border-left:1px solid #f9f9f5;
  border-right:1px solid #f9f9f5}
.vbclean_postbitmsgfg{
  background:#FFFFFf; padding: 0 5px;}


.vbclean_msgtext
{
	color: #000000;
}
.vbclean_msgtext a:link, .vbclean_msgtext_alink
{
	color: #444;
	text-decoration: underline;
}
.vbclean_msgtext a:visited, .vbclean_msgtext_avisited
{
	color: #444;
	text-decoration: underline;
}
.vbclean_msgtext a:hover, .vbclean_msgtext a:active, .vbclean_msgtext_ahover
{
	color: #c00;
	text-decoration: underline;
}

.vbclean_prefix
{
	color: #c00;
	font: 12px Ubuntu, Arial, Sans-Serif;
}

#searchbox {
width:50%;
height:25px;
text-align:right;
line-height:60px;
position:absolute;
top:6.5em;
right:30px;
}

#searchbox p {
line-height:1.1em;
position:absolute;
bottom:0;
right:0;
}

#searchbox button {
background-color:#fff;
background-image:url(http://tyrion.library.utah.edu/icon-newsearch.png);
width:20px;
background-repeat:no-repeat;
background-position:center;
border-style:none;
}

#searchbox button span {
display:block;
text-indent:-100px;
overflow:hidden;
}

#searchbox input {
border:1px solid #C6C6C6;
color:#777;
font-size:12px;
padding:2px;
}

.vbclean_notice{display:block}
.vbclean_notice *{
  display:block;
  height:1px;
  overflow:hidden;
  font-size:.01em;
  background:#C03736}
.vbclean_notice1{
  margin-left:3px;
  margin-right:3px;
  padding-left:1px;
  padding-right:1px;
  border-left:1px solid #e9f6cd;
  border-right:1px solid #e9f6cd;
  background:#d9f0a8}
.vbclean_notice2{
  margin-left:1px;
  margin-right:1px;
  padding-right:1px;
  padding-left:1px;
  border-left:1px solid #fafdf3;
  border-right:1px solid #fafdf3;
  background:#d6eea1}
.vbclean_notice3{
  margin-left:1px;
  margin-right:1px;
  border-left:1px solid #d6eea1;
  border-right:1px solid #d6eea1;}
.vbclean_notice4{
  border-left:1px solid #e9f6cd;
  border-right:1px solid #e9f6cd}
.vbclean_notice5{
  border-left:1px solid #d9f0a8;
  border-right:1px solid #d9f0a8}
.vbclean_noticefg{
  background:#C03736;
  padding: 0 5px;
  color: white;}

.vbclean_msgtags {
font:11px Verdana, Arial, Tahoma;
color:#3979A3;
}
.stickybg
{
	background-color: #ffffff;
}

span.forumhome_stats {border:none !important;}

hr { opacity: 0.2 !important; color: #dd4814 !important; height: 1px !important; border-bottom: 0px !important; border-left: 0px !important; border-right: 0px !important; }

.page > div > table { border-radius: 8px; }
.page > div > form > table { border-radius: 8px; }
```

---

### Post by bodhi.zazen on 2012-05-10
I do not have time to digest the entire css at the moment, and to be honest, I am not sure what changes you want to make (colors, etc).

I suggest you add !important to the sections that are not working (navbar, New Reply and forum titles).

Try the New Reply first (assuming you have the colors defined properly).

```
color: #FFFFFF !important;
background:#efefe3 !important;
```

---

### Post by davidvandoren on 2012-05-11
I am pretty sure you already know this, but just in case.

You should use firebug [http://getfirebug.com/](http://getfirebug.com/)

---


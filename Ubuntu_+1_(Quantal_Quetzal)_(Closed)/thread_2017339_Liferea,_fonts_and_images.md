---
title: "Liferea, fonts and images"
date: 2012-07-05
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Elfy on 2012-07-05
Liferea appears to be not using fonts set in system for the panel you read the feed in.

Anyone else seeing this? 

[img]http://ubuntuforums.org/attachment.php?attachmentid=220704&stc=1&d=1341482770[/img]

[https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/1021227](https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/1021227)

---

### Post by Toz on 2012-07-05
I'm not seeing the same issue. Is there anything in your ~/.liferea_1.8/liferea.css file that is specifying a font?

---

### Post by Elfy on 2012-07-05
> **Toz said:**
> I'm not seeing the same issue. Is there anything in your ~/.liferea_1.8/liferea.css file that is specifying a font?

Not that I know of - but it's all voodoo to me I'm afraid :)

```
/**
   This is a template file which you can use to redefine the Liferea
   CSS definitions use to render items. Below you find empty class
   definitions including comments describing what they are used for.
  
   Before you start customizing...

   Reloading:
   ==========

   For performance reasons Liferea will read this CSS file only 
   on startup. So when you modify it please restart Liferea for
   changes to take effect.

  
   About Font Definitions: 
   =======================
 
   You should avoid setting absolute font sizes. This allows Liferea
   to follow the GNOME font and font size. Use relative definitions
   instead (e.g. "1.2em" or "0.8em").

   
   Color Definitions:
   ==================
   
   Try to reuse GTK theme colors. Liferea uses the following definitions
   and will be replace them on the fly:
   
       GTK-COLOR-FG
       GTK-COLOR-BG
       GTK-COLOR-LIGHT
       GTK-COLOR-DARK
       GTK-COLOR-MID
       GTK-COLOR-BASE
       GTK-COLOR-TEXT
       GTK-COLOR-NORMAL-LINK
       GTK-COLOR-VISITED-LINK


   Inspecting the HTML:
   ====================

   If the definitions below do not help you, run Liferea with
   the parameter "--debug-html". Then Liferea will dump HTML
   into 

          ~/.liferea_1.8/output.xhtml

   each time it renders an item or a feed. So you can check for
   style classes and the layout you want to affect.

 */

/* Item display rendering header table (with title, categories...) */
// table.itemhead { }

/* Feed display rendering header table (with title, categories...) */
// table.feedhead { }

/* Left <td> of feed/item table display containing favicon */
// td.headleft { }
// a.favicon { }
// a.favicon img { }

/* Right <td> of feed/item table display containing title */
// td.headright { }

/* Metadata display table (inside header table) */
// table.headmeta { }

/* 2 pane mode: Item menu definitions */
// .itemmenu { }
// .itemmenu a { }
// .itemmenu a:hover { }
// .itemmenu * span { }
// .itemmenu * img { }

/* Header table fields to different item metadata */
// .author, .categories, .source { }
// .date { }

/* Item/feed description */
// div.content { }

/* Comment rendering */
// div.comment { }
// div.comment_body { }
// div.comment_title { }

/* Styles for the HTTP error box at the beginning
   of the feed description and for item comment feeds */
// #errors, #commentFeedError { }
// #parseError, #filterError, #updateError { }
// div.xmlparseroutput { }
// span.details, span.detaillink { }
// span.details { }
// span.showmore { }

/* namespace specific styles */
// div.blogchanneltitle { }
// div.photoheader { }

/* Gravatar embedding */
// img.gravatar { }

/* OpenStreeMap embedded map*/
// #map img { }

/* Slashdot Header */
// .slash { }
// .slashSection, .slashDepartment { }
// .slashValue { }
```


Edit - unless it's this bit in /home/hobgoblin/.liferea_1.8/cache/style.css


```
/**
 * @file liferea.css  Liferea rendering stylesheet
 *
 * Copyright (C) 2004-2010 Lars Linder <lars.lindner@gmail.com>
 * Copyright (C) 2004 delusional <delusional@dx13.co.uk>
 *
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 2 of the License, or
 * (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA 
 *
 */

/* 

   Font Definitions: 
   =================

   No style definition should set absolute font sizes,
   font families or line heigth and spacing. This is to allow a GNOME
   preference controlled default font size. 
   
   Color Definitions:
   ==================
   
   To allow using GTK theme colors the following key words 
   will be replaced with the corresponding GTK theme color values:
   
   3C3C3C
   CECECE
   FFFFFF
   909090
   C8C8C8
   FCFCFC
   000000
   74A0C6
   000000
 */

body {
	background: #FCFCFC;
	color: #000000;
	padding:0;
	margin:0;
}

blockquote {
        border-left: 2px solid #909090;
        background: #CECECE;
        padding: 5px;
        font-style: italic;
        margin: 5px 20px;
	clear:both;
}

a {
	color: #74A0C6;
}

a:visited {
	color: #000000;
}

dd {
	padding-left: 30px;
}

img {
	border:0;
	margin:2px;
}

img.gravatar {
	/* gravatars have align="left" so we need proper margin */
	margin-right:12px;
}

#map img {
	/* OpenStreeMap map tiles must have no border */
	border:0px;
	margin:0px;
}

/* styles for the item description (currently also used for
   the feed description) */
table.itemhead, table.feedhead {
	margin:0;
	width:100%;
	border:0;
	border-bottom: 1px solid #909090;
	clear:both;
	color:#000000;
}

.itemhead, .feedhead {
	background-color: #C8C8C8;
}

table.itemhead * td {
	padding: 2px;
	padding-top: 4px;
}

table.itemhead * a.itemhead {
	text-decoration:none;
	color:#000000;
	font-weight:bold;
}

td.headleft {
	text-align:right;
}

td.headright {
	padding:2px 5px;
}

table.headmeta {
	background:#CECECE;
	width:100%;
	border:0;
	border-bottom:#C8C8C8 solid 1px;
	margin:0;
}

table.headmeta td {
	padding:1px 6px 1px 12px;
	font-size:0.8em;
}

.hidden {
	visibility:hidden;
	display:none;
}

.itemmenu {
	margin:0;
	padding:0;
}

.itemmenu a {
	text-decoration:none;
	color:#000000;
}

.itemmenu a:hover {

}

.itemmenu * span {
	font-size:1em;
[COLOR="Red"]	font-family:sans-serif;[/COLOR]
	padding:0;
	margin:0;
	position:relative; 
	top:-3px;
}

.itemmenu * img {
	padding:0;
	margin:0;
	height:16px;
	position:relative; 
	top:1px;
}

.author, .categories, .source {
        padding:0;
	margin-left:0;
        margin-right:12px;
}

.date {
	white-space:nowrap;
	text-align:right;
	padding-right:5px;
}

div.content {
	padding:0px 6px 0px 12px;
}

div.comment {
	border:1px solid #909090;
	margin-bottom:5px;
}

div.comment_body {
	padding-left:6px;
	padding-right:6px;
}

div.comment_title {
	padding-left:6px;
	padding-right:6px;
	font-weight:bold;
	background:#CECECE;
}

a.favicon {
	text-decoration:none;
}

a.favicon img {
	width:16px;
	border:0;
	margin:0;
	padding:0;
}

/* styles to realize shading of new items in condensed mode */
.itemshaded { background:#ffe; color:black; padding:1px; margin:0; }

.itemunshaded { padding:1px; margin:0; }

.summaryshaded, .summaryunshaded { 
	padding:0px 6px; 
	margin:0;
}

.summaryshaded a {
	display:block;
	background:#ffe;
	color:black;
	text-decoration:none;
	padding:1px 0px;
	font-weight:bold;
}

.summaryunshaded a {
	display:block;
	color:#000000;
	text-decoration:none;
	padding:1px 0px;
}

.summarytime {
	padding-right:15px;
	white-space:nowrap;
	color:#999;
}

hr.summary {
	border:0;
	padding:0;
	margin:2px;
	border-bottom:1px dashed #ddd;
}

/* style for the HTTP error box at the beginning
   of the feed description and for item comment feeds */
#errors, #commentFeedError {
	width:100%;
	border:0;
	border-bottom:1px solid black;
	margin:0;
	background:#ffa;
}

#commentFeedError {
	border:1px solid black;
}

#parseError, #filterError, #updateError {
	padding:2px;
	padding-left:5px;
	padding-right:5px;
}

div.xmlparseroutput {
	margin:10px 0px 10px 15px;
	padding:5px;
	border:2px solid #909090;
	background:#FFFFFF;
}

span.details, span.detaillink {
	visibility:hidden;
	display:none;
}

span.details {
	padding:5px;
	margin:15px;
}

span.showmore {
	text-decoration:underline;
	color:blue;
	cursor:pointer;
}

del {
	text-decoration: line-through;
}

ins {
	text-decoration: underline;
}

/* namespace specific styles */
div.blogchanneltitle {
	padding-left:10px;
	padding-right:10px;
	background-color:#909090;
	color:#000000;
}

.slash {
	background:#60A080;
	padding-left:5px;
	padding-right:5px;
}

.slashSection, .slashDepartment {
	padding-right:2px;
	color:black;
}

.slashValue {
	padding-right:6px;
	color:white;
	font-weight:bold;
}

div.photoheader {
	margin:10px 0;
	padding-left:10px;
	padding-right:10px;
	background-color:#909090;
	color:#000000;
}


/*
 * Liferea ad blocking stylesheet
 *
 * (C) 2005-2007 Lars Linder <lars.lindner@gmail.com>
 *
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 2 of the License, or
 * (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA 
 *
 */

iframe[src="kanoodle"],
*[src*="imageads.google"],
*[href*="doubleclick"] img, *[src*="doubleclick"],
*[href*="feedstermedia.com/feedster/adclick.php?bannerid="]
{ display:none !important; visibility:hidden; margin:0; }

div.feedflare { display: none !important; visibility:hidden; margin:0; }

img[width="468"] { display: none !important }
img[width="1"] { display: none !important }

```

---

### Post by Toz on 2012-07-05
Our files are similar. Try copying over the default css file and making a font change:

```
cp /usr/share/liferea/css/liferea.css ~/.liferea_1.8
```
...edit the ~/.liferea_1.8/liferea.css file and add to the top of the file:
```
* {
	font-family: "comic sans ms";
}
```

Feel free to change "comic sans ms" to any font you want. 

The above worked for me in that my item text was now in comic sans format.

---

### Post by Elfy on 2012-07-06
That fixed it - thanks Toz

---

### Post by Elfy on 2012-07-10
Changed title of thread as staff are wont to do from time to time.

Liferea refusing to display images.

There are a few references about - none of which appear to help here, however I installed blam - to look

It, too, refuses to display images.

---

### Post by Toz on 2012-07-10
Hi Elfy. 
Interesting that neither liferea nor blam display images. They both use webkit to display - maybe your issue lies with webkit?

---

### Post by Elfy on 2012-07-11
Checked 1210 and 1204 packages - ensured same installed in both. No change.


[https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/1023038](https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/1023038)

Somethinh must have been updated - all works now.

---

### Post by jonson_7 on 2012-09-14
Hey

Im still having the described issues with Liferea and Blam  :(
also my twitter clients Hotot and Turpial doesnt work eather. 

What happens is this:

[I]Liferea:
- Doesn't show any pictures

Blam Feed Reader:
- Doesn't show any pictures

Hotot Twitter Client:
- Tels me "Access token doesn't exists"

Turpial:
- Tels me: "Unable to load page
Problem occurred while loading the URL [https://api.twitter.com/oauth/authorize?oauth_token=G4jU0vgkAguquHL9WBICVwqElpAZYN18oC6rlKdcEMg](https://api.twitter.com/oauth/authorize?oauth_token=G4jU0vgkAguquHL9WBICVwqElpAZYN18oC6rlKdcEMg)
Cannot resolve proxy hostname ()"

Pidgin Internet messenger:
- Works just fine :)

gpodder Podcast Client:
- Doesn't show pictures[/I]

I havent set up any special proxy-settings to mu knowledge.  Does anyone have a clue about what's going on?

---


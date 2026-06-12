---
title: "SSI on apache2"
date: 2006-11-15
forum: Server Platforms
---

### Post by maniacmusician on 2006-11-15
hey,

I'm trying to enable SSI on a local apache2 setup. I followed some common instructions I found, but doesn't look like it's working. I'm pretty new to this though, so it could be possible I just goofed. Here's my /etc/apache2/httpd.conf

```

# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

Options +Includes
AddType text/html .shtml
AddOutputFilter INCLUDES .shtml


```

I think that's all you need right? just ask if you need another conf file.

---

### Post by maniacmusician on 2006-11-16
anyone? This shouldn't be very hard, right?

---

### Post by DRicher33 on 2006-11-16
Hi,

What error are you getting exactly?

---

### Post by maniacmusician on 2006-11-16
I'm not getting an error; my SSI's are just not displaying on localhost, like I need them to.

---

### Post by maniacmusician on 2006-11-19
can someone please help? it's really a huge pain having to constantly re-upload files to the net just to see if everything is working or not :(

---

### Post by MJN on 2006-11-21
Try putting those directives inside your <Virtualhost></Virtualhost> directives (in /etc/apache2/sites-available/default) as opposed to httpd.conf.

As the header says that file exists for backwards compatibililty and hence you shouldn't really be putting directives in there yourself (sure, the file is parsed by apache2.conf but do the job properly! ;)). Instead, use apache2.conf or, for directives that need to be applied on a Virtualhost-by-Virtualhost basis (this may be the case here), put them inside the <Virtualhost> containers as mentioned. In fact, the **Options +Includes** directive must go inside the <Directory> container (inside <Virtualhost>).

If none of this makes sense, post the contents of /etc/apache2/sites-available/default and we can edit to suit.

Also, it's got to be asked, do you have the mod_include module loaded? That is, did you do execute **a2enmod include**?

Mathew

---

### Post by tturrisi on 2006-11-21
I believe the ssi module must also be loaded as well.  You will see the module in /etc/apache2/mods-available and you will need a symlink to it in /etc/apache2/mod-enabled, then restart apache2.

---

### Post by MJN on 2006-11-21
SSI module? Are you sure you haven't mistaken the 'L' for an 'I' in the *ssl* module? ;)

Mathew

---

### Post by tturrisi on 2006-11-21
> **MJN said:**
> SSI module? Are you sure you haven't mistaken the 'L' for an 'I' in the *ssl* module? ;)

Mathew
oops! You're right, my bad.

---

### Post by maniacmusician on 2006-11-21
> **MJN said:**
> Try putting those directives inside your <Virtualhost></Virtualhost> directives (in /etc/apache2/sites-available/default) as opposed to httpd.conf.

As the header says that file exists for backwards compatibililty and hence you shouldn't really be putting directives in there yourself (sure, the file is parsed by apache2.conf but do the job properly! ;)). Instead, use apache2.conf or, for directives that need to be applied on a Virtualhost-by-Virtualhost basis (this may be the case here), put them inside the <Virtualhost> containers as mentioned. In fact, the **Options +Includes** directive must go inside the <Directory> container (inside <Virtualhost>).

If none of this makes sense, post the contents of /etc/apache2/sites-available/default and we can edit to suit.

Also, it's got to be asked, do you have the mod_include module loaded? That is, did you do execute **a2enmod include**?

Mathew
I don't know if I have the mod_include module loaded...I didn't consciously load it, or install anything to do so, so I'm assuming not. I'm guessing I have to do this, because I added those lines, and that hasn't worked. (yes, I did restart apache)

Here's what my sites-enabled/default looks like after I put that stuff in:

```
 
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews +Includes
                AddType text/html .shtml
                AddOutputFilter INCLUDES .shtml
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


```

Thanks a lot for replying

---

### Post by MJN on 2006-11-21
It sounds like you're simply missing the include module.

To check, have a look in /etc/apache2/mods-enabled/ and you should see an **include.load** symlink. If not, run **sudo a2enmod include** and it'll put it in for you (thus loading the module when you restart Apache).

Mathew

---

### Post by maniacmusician on 2006-11-21
Thank you so much! Finally!! This will save me a LOT of work as I use SSI's quite liberally. Thank you, thank you, thank you. 

This is great. Thank you! *works on the site faster than ever*

---

### Post by MJN on 2006-11-22
You're welcome.
 
You might also be interested in the 'XBitHack' variation of SSI's - a mechanism whereby 'standard' HTML documents (.htm/.html) can benefit from SSI's on a file-by-file basis - this is done by setting the execute bit on the file in question. Hence, you don't need to specifically name files with an .shtml extension (this may not be an issue for you though).
 
Further details at [http://httpd.apache.org/docs/2.0/howto/ssi.html](http://httpd.apache.org/docs/2.0/howto/ssi.html)
 
Mathew

---

### Post by maniacmusician on 2006-11-22
no, it's not an issue for me, but it's extremely interesting stuff, and always good to know. Thanks for the heads-up. 

If you want to see the quick work your help has inspired, here's the link. I've only really been working on the "client" site (it's not finished), and of course the site as a whole isn't finished yet either. [http://dohickey.sourceforge.net](http://dohickey.sourceforge.net)  

One thing I have to fix is styling that "Search" button on the main page. Last time I was using google, I saw a tutorial on how to do that with javascript, so I'll definitely be looking that up once more. Anyways, thanks again for your help.

---

### Post by MJN on 2006-11-22
Looking good - nice and clean!

---

### Post by tturrisi on 2006-11-22
Looks much better than the last time I saw it, good job.
But the css layout is still a bit funky on the client page.  The class='page' is fixed at a width that will produce horiz scrollbars in most browser windows, horiz scrollbars really suck per www user surveys, myself included.  Altering that width messes up the layout.

---

### Post by maniacmusician on 2006-11-24
yes that's true. I couldn't however think of a better way to control it...I've made all the items as small as possible and the current width is as small as it gets. I know horizontal scrollbars suck, I don't like them either. (if it's any consolation, they don't show up on higher resolution screens, like 1400x1050, or even 1280x1024)

---

### Post by tturrisi on 2006-11-24
> **maniacmusician said:**
> yes that's true. I couldn't however think of a better way to control it...I've made all the items as small as possible and the current width is as small as it gets. I know horizontal scrollbars suck, I don't like them either. (if it's any consolation, they don't show up on higher resolution screens, like 1400x1050, or even 1280x1024)
I understand, I fought w/ similar issues before, pulled my hair out, lost sleep, drteamed about solutions, etc!
What I do now when I want a page w/ 3 columns of data where I can control theb positioning of stuff in each column is use css divs instead of tables for the containers. Save the below as columns.html and see what I am talking about.  The code is really quite simple.
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">

<html>

<head>

<title>Demo: CSS 3 Column Layout</title>
<style type="text/css">

body {font-family:sans;
text-size:100%;
margin:10px;}

.heading {border: solid 1px blue;
height:80px;
text-align:center;
vertical-align:middle;}

.container {
width:100%;
margin:0px;
background:#ffffff;}

.left {
width:170px;
margin:0px;
float:left;
padding-top:20px;
border: solid 1px green;}

.right {
width:200px;
margin:0px;
float:right;
border: solid 1px black;}

.middle {
width:auto;
background:#ffffff;
border: solid 1px red;
margin-top:0px;
margin-left:170px;
margin-right:200px;
padding-top:10px;
padding-left:20px;
padding-right:20px;
padding-bottom:20px;}
</style>
</head>
<body>
<!-- BEGIN HEADING --><div class="heading"><h1>CSS 3 Column Layout</h1></div><!-- END HEADING -->

<!-- BEGIN CONTAINER --><div class="container">

<!-- BEGIN LEFT COLUMN --><div class="left">
<h3 style="text-align:center">Left Column</h3>
<p style="height:300px; width:130px; padding:10px; text-align:center;">Link<br>Link<br>Link<br>Link<br>Link<br>Link<br>Link</p>
</div><!-- END LEFT COLUMN -->

<!-- THIS RIGHT DIV MUST PRECEDE THE MIDDLE DIV -->
<!-- BEGIN RIGHT DIV --><div class="right">
<h3 style="text-align:center">Right Column</h3>
<p style="height:200px; width:180px; padding:10px; text-align:center;">Thisn is a good spot for RSS feeds, news, weather, dynamic content, etc. etc.</p>
</div><!-- END RIGHT DIV -->

<!-- BEGIN MIDDLE DIV --><div class="middle">
<h3>Middle Column</h3>
<p>Anything can go here, such as tables, lists, images, the main content of the page. This middle column is scalable to the browser window, the left & right columns have fixed widths and will move when the browser window size changes, but the content in them does not scale beyond the column borders.</p>
<p>For demonstration purposes, the left and right columns have fixed heights, but on a real site the heights need not be fixed. The divs have different color borders, borders do not need to be used.</p>
<p>A document using this layout will look good in any size browser window. The important thing to remember is to count pixels when adding content.  For example, at a screen resolution of 800x600, the maximum available width of the middle column is approx 400 pixels.  Content wider than that will result in a horizontal scrollbar in the browser.</p>
<p>This is not really an issue because text will scale to the column width, as will any other element whose dimensions are set using percentages. The only concern is if use an image that is wider than the available column width.</p>
<p><img scr="" width="400" height="300" alt="this empty image is 400 pixels width and 300 pixels height">
</div><!-- END MIDDLE DIV -->

</div><!-- END CONTAINER -->
</body>
</html>
```

---

### Post by maniacmusician on 2006-11-24
I havn't actually viewed it as a page yet, but I can see what the code would do. I have to say though, isn't the container <div> a lot like my page <div>? They both strive to bind everything on the page into one neat section.

Anyways, my setup is already really similar to what you have shown right there. To get your effect, I'm thinking all I would have to do is change the width of .page to 100%, leave the widths of .nav and .stats as they are, and then change the width of .main (the middle part) to auto. Would that not work? I'll try it later this weekend to see if it does. Thanks for the heads up.

---

### Post by tturrisi on 2006-11-24
Yeah, the middle section needs to be set to auto.

But the key difference between yours & mine is using the combination of float & margin.  The left div floats left, the middle dive has a margin-left that is the width of the left div and it has a margin-right that is the width of the right div, and the right div floats right.  The middle div 'allows" the left & right to fit in the container.

The key though (in order to work in all browsers) is the order in which the elements get displayed.  The right div section of code must come before the middle div code in the document, else the middle section will "drop" and display beneath the rt div.

another tip:
You can eliminate the bouble breaks in the menu <br><br> by using the css for class menu_item:
display:block;
margin-bottom:20px; (or desired distance between)

Sorry, I did email support for a developer's web editor for 4 yrs, so I am in the habit of reviewing the code!

---

### Post by maniacmusician on 2006-11-24
quite alright my friend, a little criticism has never hurt anyone. in fact, your help from last time was a big part of getting the site to look better, and this new info will come in handy as well. I'm not going to try anything with it right now, I'm dead tired and a little drunk.

I hear ya about being careful about which order the elements get displayed in though. I had a LOT of trouble with that when I first began. 'twas a nightmare. But I've learned. Using SSI's has made my life a lot easier, as it saves a substantial amount of time. thanks again for the advice, I'll fiddle around with the code some more later.

---

### Post by tturrisi on 2006-11-25
Thanks!
Most do not take constructive criticism as sincere.
fyi, if ever stumped by ssi again, or want to use something other than ssi, an option is to use php includes, which are not controlled by apache ssi.

On a .php page the code would be:
include ("../inc/some-file.php");  or
include ("../inc/some-file.js");  or
include ("../inc/some-file.xxx");

On a html page the embedded php code would be:
<table class="left_nav">
<tr><td class="the_menu"><? include("inc/menu.html") ?></td></tr>
</table>

The menu.html doc would consist only of the links tags (no <html><head><body> tags), which is very useful on a large menu, just one file to edit & upload.  Plus, the included doc w/ static content gets cached by the browser and makes pages load super fast.

Javascript does this too, but that can be affected by the client settings.

One more question:
Is that a pic of you in the avatar?

---

### Post by maniacmusician on 2006-11-25
> **tturrisi said:**
> Thanks!
Most do not take constructive criticism as sincere.
fyi, if ever stumped by ssi again, or want to use something other than ssi, an option is to use php includes, which are not controlled by apache ssi.

On a .php page the code would be:
include ("../inc/some-file.php");  or
include ("../inc/some-file.js");  or
include ("../inc/some-file.xxx");

On a html page the embedded php code would be:
<table class="left_nav">
<tr><td class="the_menu"><? include("inc/menu.html") ?></td></tr>
</table>


Thanks, but I've heard php is a whole another league, and can be very eccentric. Not sure I'm quite ready to dive into it. I was considering tackling JS next.

> **tturrisi said:**
> 
The menu.html doc would consist only of the links tags (no <html><head><body> tags), which is very useful on a large menu, just one file to edit & upload.  Plus, the included doc w/ static content gets cached by the browser and makes pages load super fast.

Yes, I'm pretty sure that's just the way SSI's work too. Incredibly useful.
> **tturrisi said:**
> 
One more question:
Is that a pic of you in the avatar?
No, unfortunately ;) it's not.

---


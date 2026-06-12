---
title: "HOWTO: Getting Started with Linux Standalone Apps using XUL"
date: 2007-01-08
forum: Tutorials
---

### Post by SuperMike on 2007-01-08
[SIZE="4"]**Introduction**[/SIZE]

Perhaps there's a developer out there who knows web development, but hasn't really done many standalone applications or doesn't have the time to learn the API for that, and who wants to make a standalone application on Ubuntu Linux. Perhaps this developer is you. If so, then read on.

If you look around, most of the standalone apps running on Linux since about 2002 are being created in Python with PyGTK or PyQT. This is great and all if you know Python and are willing to learn the documented and undocumented (or at least hard-to-find facts) about PyGTK or PyQT API for drawing the GUI. The technique presented here is different, however, and will show you how to get started in writing standalone Ubuntu software in Javascript and HTML, and to use SQLite as your database.

Here's a small example of what it looks like:

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=22516&d=1168242696[/IMG]

[SIZE="4"]**Development Environment Installation**[/SIZE]

After temporarily turning on your Universe option in /etc/apt/sources.list, run this:

[FONT="Fixedsys"]$ sudo apt-get install ngs-js
$ sudo apt-get install thttpd*
$ sudo apt-get install sqlite3*[/FONT]

...and then turn off your Universe option.

When this is installed, you'll want to ensure (using find, whereis, or whatever) that these commands are put in the places that I expect them to be:

[FONT="Fixedsys"]/usr/bin/ngs-js
/usr/sbin/thttpd
/usr/bin/sqlite3[/FONT]

If not, then you may want to either adjust the scripts below or make links (using 'ln' command) in these places so that things are called properly.

[SIZE="4"]**Getting Started**[/SIZE]

To build a short example to get started, we need just 4 files:
[LIST]
[*]names.sql - the script to create our database if it doesn't exist
[*]example.xul - the GUI description
[*]example.js - the application's starting page
[*]example - the bash script that kicks the process off
[/LIST]

**names.sql**
```
DROP TABLE names;
CREATE TABLE names (
 firstname varchar(60),
 lastname varchar(60)
);
INSERT INTO names VALUES ('Marty','Mouse');
INSERT INTO names VALUES ('Spidey','Man');
INSERT INTO names VALUES ('Duck','McDuff');
INSERT INTO names VALUES ('Super','Coolman');
INSERT INTO names VALUES ('Test','Tester');
```

**example.xul**
```
<?xml version="1.0"?>
<?xml-stylesheet href="chrome://global/skin/" type="text/css"?>
<window
id = "myapp"
title = "SQLite Example"
height = "420"
minHeight = "420"
width = "640"
minWidth = "640"
screenX = "10"
screenY = "10"
sizemode = "normal"
wait-cursor = "false"
xmlns = "http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul" >
<spacer style = "height: 4px; cursor: default;" />
<hbox flex = "1">
<iframe
id = "webframe"
flex = "1"
src = "http://127.0.0.1:11255/example.js"
style = "border: 0px" />
</hbox>
</window>
<!-- type = "content-primary" -->
```

**example.js**
```
#!/usr/bin/ngs-js

var $LastError = '';
var $_bAlreadyWrittenContent = 0;

function echo($sMsg) {
        if (!$_bAlreadyWrittenContent) {
	        System.stdout.writeln("Content-type: text/html\r\n");
	        $_bAlreadyWrittenContent = 1;
        }
        System.stdout.write('' + $sMsg);
}

function DBQuery($sDBFile, $sSQL) {
        $oPipe = System.popen("/usr/bin/sqlite3 -header -separator '< >' -nullvalue '<NULL>' " + $sDBFile + " '" + $sSQL + "'", 'r');
        $i=0; $bError=0; $sBuild = '';
        $aRows = new Array();
        $aRow = new Array();
        while (!$oPipe.eof()) {
                $sLine = $oPipe.readln();
                if ($sLine == '') {
                        break;
                }
                if (($sLine.indexOf('error') != -1) || ($bError=1)) {
                        $bError = 1;
                        $sBuild += $sLine;
                }
                $aRows[$i] = $aRow.concat($sLine.split('< >'));
                $i++;
        }
        $LastError = $sBuild;
        return $aRows;
}

function Main() {
	echo("<style>\n");
	echo("BODY {\n");
	echo(" background: #f7f7f7");
	echo("}\n\n");
	echo("TABLE {\n");
	echo(" border-collapse: collapse;\n");
	echo(" white-space: nowrap;\n");
	echo(" font-family: Arial,sans;\n");
	echo(" font-size: 9pt;\n");
	echo("}\n\n");
	echo("TD,TH {\n");
	echo(" border: 1px Gainsboro solid;\n");
	echo(" padding-left: 8px;\n");
	echo(" padding-right: 8px;\n");
	echo(" background: #ffffff;\n");
	echo("}\n\n");
	echo("TH {\n");
	echo(" background: #000000;\n");
	echo(" color: #ffffff;\n");
	echo("}\n\n");
	echo("TH P {\n");
	echo(" text-transform: capitalize;\n");
	echo("}\n\n");
	echo(".tdalt {\n");
	echo(" background: #e9e9e9;\n");
	echo("}\n\n");
	echo("</style>\n");
	$rsRows = DBQuery('names.db','select * from names');
	echo("<TABLE BORDER=0 CELLSPACING=0 CELLPADDING=0>\n");
	$i = 0;
	for ($asRow in $rsRows) {
			echo("<TR>\n");
	        for ($sColVal in $asRow) {
	        		if ($i == 0) {
	        			echo('<TH><P>' + $sColVal + '</P></TH>');
	        		} else {
	        			if ($i % 2) {
			                echo("<TD class='tdalt'>" + $sColVal + '</TD>');
			            } else {
			            	echo('<TD>' + $sColVal + '</TD>');
			            }
		            }
	        }
	        $i++;
	        echo("\n</TR>\n");
	}
	echo("</TABLE>\n");
}

Main();
```

**example**
```
#!/bin/bash

PATH=$PATH:"$PWD"
chmod a+x example.js
if [ ! -f names.db ]; then
        sqlite3 -init names.sql names.db '.quit' 2>&1 > /dev/null
fi
thttpd -d "$PWD" -p 11255 -c '**.js' -l /tmp/thttpd.log
firefox -chrome file:$PWD/example.xul
```

Drop these files into a directory under your ordinary user account and run the application like so:

[FONT="Fixedsys"]$ sh example[/FONT]

The result you get is like the attached example.png to this article.

**How The Example Works**

First, we load the example Bash script and in general it creates a names.db database file if one doesn't exist, launches a small, embeddable web server (thttpd) on port 11255, and then launches a Firefox *process* with an exclusive GUI file called a *chrome*.

When Firefox is loaded in this manner, it does not display anything except what we specify in the XUL file. Now the XUL format is extremely rich but it can get very complex to work with it. It can support a whole list of GUI widgets that can dazzle you. If you're interested in that, see the references link at the bottom of the article. For me, I wanted to go a different route because I wanted to build applications that use what I am used to using -- Javascript and HTML instead of all this complex XUL. Therefore, as you can see in the XUL file, once we set the window properties, we load an HTML browser widget inside that immediately attaches to the web page (example.js) from the tiny web server.

This web server operates like a normal CGI web server and so you'll want to understand a little how CGI works if you want to do things like page redirection, form handling, and so on. A reference for that is at the bottom of this article. Since CGI can be slightly difficult, once I figure something out, such as page redirection, I throw it into a web.js file as a function so that I can refer to it routinely instead of remembering how to do it on a line-by-line CGI level.

Because you may have web apps hosted on a usual port like 80 or 443, we don't use that for our port. You have a range of 7000-65535, usually, for web apps on alternate ports, so we chose 11255. However, if you have more than one of your apps loaded, you'll need each one on an exclusive port or you'll cause a conflict with the example scripts. (The other technique is to use different directories.) If you're using a local workstation firewall, you'll want to open up port 11255. I use an iptables script, so I stuck this into it:

[FONT="Fixedsys"]# XUL apps
iptables -A INPUT -p tcp -m tcp --dport 11255 --syn -j ACCEPT
iptables -A INPUT -p udp -m udp --dport 11255 -j ACCEPT[/FONT]

Note that the example Bash script calls thttpd and doesn't worry about the fact that it may already be in memory. This is because thttpd is smart and won't let itself be loaded more than once on the same port. 

Note also that I don't stop thttpd when the GUI is closed when you click X. This is because I don't currently know how to detect what window titles are open on the X terminal, and testing for an instance of firefox in memory won't cut it because someone may be using firefox to do web surfing in addition to loading your XUL application. _So, if you know how to catch this and stop the thtpd server, please reply to this article to show us all how._ It's a minor thing to have this thttpd service running on an alternate port if you're behind a subnet or a firewall, but I really would like to learn how to stop this service once the XUL application is closed.

The web server calls our Javascript file, example.js, and because our example Bash script set it to executable, the web server will run it instead of display it as text in the browser. And inside example.js, a critical line was:

[FONT="Fixedsys"]#!/usr/bin/ngs-js[/FONT]

That tells the shell what command to use to run this script. The NGS-JS project is sort of a stale project since around 2004, last I saw, but the amazing thing is that it works extremely well as a Javascript interpreter with the power to shell out to other processes, read/write files, and so on. It is written in C. The thing to understand about NGS-JS is that you first must understand Javascript fairly well, and then learn the extra stuff in NGS-JS that it does beyond standard Javascript.

From our example.js, it loads a Main() function which builds a style sheet, queries the database, and iterates the result in an HTML table.

To make things a little easier for myself with the Javascript, if there's a function or set of functions I tend to call frequently, and if I know the equivalent of that in my language of choice (PHP), then I encapsulate that into a function that tries to look as much as like what I'm used to in my favorite language. For instance, I created an echo() function as you can see. Unlike the example above, usually I'll be putting these functions into separate files I like to call "modules", stick them in a directory called "modules", and then load these with NGS-JS's load() statement:

[FONT="Fixedsys"]load('modules/web.js');
load('modules/db.js');[/FONT]

You'll want to watch how I do that echo() function because it uses a CGI technique "Content-type: text/html\r\n" before printing text. This is necessary for your browser to display the web page properly. Otherwise, you end up with a white block on your page and nothing exciting going on.

The database query interacts with SQLite. If you're not used to this database, you should be. It's a sensational piece of work, has a great license, is free, supports a small set of ANSI-92 SQL statements, and makes for a great embeddable database in your smaller projects. For me, I use only two databases on Linux: SQLite for smaller projects or standalone applications like this, or PostgreSQL for anything else. I only use MySQL when I'm on a team project that requires it.

The way I handle the database query, since NGS-JS doesn't have a handler for it, is to use NGS-JS's System.popen() function to shell out and access our SQLite3 command. I then parse the result and stick it in an array of rows with each row containing an array of columns.

And voila!, that's how it's done.

[SIZE="4"]**Debugging**[/SIZE]

You may want to know how to debug your Javascript pages. (By the way, don't confuse Javascript pages with Java Server Pages -- these are two separate things entirely.) The way I do it is at command line like so:

[FONT="Fixedsys"]$ ngs-js example.js[/FONT]

However, typing 'ngs-js' can get tiresome. An alternate way is:

[FONT="Fixedsys"]$ ./example.js[/FONT]

...or, you can do:

[FONT="Fixedsys"]$ sudo ln -s /usr/bin/ngs-js /usr/bin/js[/FONT]

...and then do:

[FONT="Fixedsys"]$ js example.js[/FONT]

If the debugging gets too hard, you can always break out what you're trying to do into a function and then use a test script to call just that to see the result.

[SIZE="4"]**Extending - Where To Go from Here**[/SIZE]

By now, the gears are probably moving in your head and you're wondering where to go from here, such a server file read/write, drawing gadgets, AJAX, page redirection, form processing, file uploads, and a whole host of other options. Unfortunately I won't be able to cover all of this in this example, so you can ask me if you're stuck after looking at the references below.

In general, here's what you'll need to know:
[LIST]
[*]file I/O - you have two avenues -- either use System.popen() from NGS-JS and use normal Bash statements for file I/O, or use the built-in NGS-JS commands for file I/O
[*]drawing gadgets - HTML and DHTML works great, as does CSS and anything else you can do in Firefox, so you already have a rich API in the web page itself. But if it's not rich enough for you, consider reading up on XUL and adding that in. You can also use AJAX.
[*]AJAX - you can create a subfolder in your project directory called "ajax" and place your AJAX scripts in there. You can use the normal AJAX API in Firefox to interact with those pages for a result.
[*]page redirection - this is a function of CGI, but in general it looks like this:

```
function Redirect($sPageNamePath) {
        System.stdout.writeln('Content-type: text/plain');
        System.stdout.writeln('Location: ' + $sPageNamePath);
}
```

[*] form processing - this is a function of CGI and comes to you through environment variables established by the web server, which can be read like so:

```
System.getenv('QUERY_STRING');
```

...but it only works with GET type form posts. If a POST type of form post is used, you'll need to read from standard input (STDIN) by the amount of what's posted from the CONTENT-LENGTH environment variable. This is explained multiple times on the web but most of the examples are given in Perl and you have to re-interpret that in Javascript. There are also C-based GNU tools that can be used to do this for you and you can use System.popen() to shell out, get that input, and return a result back.

[*] file uploads - this gets fairly complex to describe, but is a function of CGI and requires doing a series of steps that you can find in the CGI reference below.

[/LIST]

[SIZE="4"]**Why Not Perl Instead of Javascript?**[/SIZE]

You may want to know why I don't use Perl for this example and use NGS-JS. Good point. Perl works great instead of NGS-JS, and has typically been used for CGI processing for many years, especially when web servers were just getting started on the web. However, it's all about using what you know, and many people already know a good bit of Javascript because you pretty much have to know this in order to do web development.

Another advantage of NGS-JS is that it's very small -- smaller than Perl. It makes a great, embeddable platform for standalone desktop development.

But if Perl, PHP, Python, Ruby, Pike, Scheme, or whatever language you want is your preference, then by all means do what you feel is best.

[SIZE="4"]**Conclusion**[/SIZE]

Using very minimal XUL that you write once and alter very little, and then do most of your work in Javascript, HTML, and SQL, you can produce standalone desktop applications for Linux. And if that's not good enough for you, you can add Perl, AJAX, more complex XUL, and a whole host of other options to richen the experience.

If you're bold enough, you could revise this example to make an entire Quickbooks for Small Business knockoff (badly needed, I'm afraid) standalone desktop application and many other types of standalone applications. You can also make control panels, a simulated standalone GUI for a remote website, a chat program, and all kinds of things.

[SIZE="4"]**For Further Reference**[/SIZE]
[LIST]
[*]**XUL API**
- [http://www.xulplanet.com/]("http://www.xulplanet.com/")
- [http://www.mozilla.org/catalog/architecture/xul/]("http://www.mozilla.org/catalog/architecture/xul/")
[*]**CGI API**
- [http://www.webthing.com/tutorials/cgifaq.html](http://www.webthing.com/tutorials/cgifaq.html)
- [http://hoohoo.ncsa.uiuc.edu/cgi/](http://hoohoo.ncsa.uiuc.edu/cgi/)
[*]**NGS-JS API** - [http://www.njs-javascript.org//]("http://www.njs-javascript.org//")
[*]**Javascript API** - [http://www.w3schools.com/js/default.asp]("http://www.w3schools.com/js/default.asp")
[*]**SQLite API** - [http://www.sqlite.org/]("http://www.sqlite.org/")
[*]**AJAX API** - [http://www.w3schools.com/ajax/default.asp]("http://www.w3schools.com/ajax/default.asp")
[/LIST]

Note on many of these references I recommend you use a command like wget (with the required options) to download all the pages to your local hard drive in case the site ever goes down or are no longer maintained.

---

### Post by po0f on 2007-01-08
SuperMike,

Very well put together.  One complaint: where's the screenie you mentioned?  :)  I can pretty much guess what it looks like (it's just a client-side Javascript app running in a Firefox window with regular HTML elements, correct?) but I am still curious.

---

### Post by SuperMike on 2007-01-08
Ah, I found that when it's posted to this particular forum, it doesn't display the screenshot.

Let me edit it and see if I can host it somewhere.

---

### Post by SuperMike on 2007-01-08
Mozilla now has a way to get XUL to work without a web server and, as well, has a way to interact with a database like a flat file database or a SQLite database (although others are supported). I think I see that [**Songbird**]("http://www.songbirdnest.com/"), the advanced XUL-based music player, does this. Unfortunately, I read that it requires installation of some XPCOM extensions or special compilation and that sucks. The way Songbird gets around this is by shipping an entire Mozilla distribution with Songbird and providing the extensions inside that already. It would be great if all the XPCOM stuff was already in the latest Firefox and we could just rely upon it.

If you crack open Songbird's files, you see that it was written entirely in server-less, database server-less, Javascript. When you run nmap against yourself, you also don't see it hosts any service port on your PC.

In my opinion, Songbird didn't use a KISS design -- it's a huge amount of complex code that might have been better implemented in less code. Also, because the interface was done entirely in XUL, rather than XUL calling HTML, that made it even more complex.

---

### Post by SuperMike on 2007-01-08
Probably the most efficient way to build these applications is to store them all as subdirectories under:

/usr/share

...like other programs do and then have the thttpd command refer to /usr/share as the home directory and the XUL to refer to something like myapp/index.js. Then, use the same thttpd and port for all the apps to share so that you don't have more than one thttpd in memory at once.

---

### Post by SuperMike on 2007-01-08
Building menus can be done in XUL, of course, but that drives up the complexity. Besides, you may already be used to doing menus in CSS, dhtml, or Javascript by now. My taste is to do the menus in [**[COLOR="DarkOrange"]pure CSS[/COLOR]**]("http://meyerweb.com/eric/css/edge/menus/demo.html") and don't worry about the fact that this won't work well on IE because we're using Firefox instead.

I've also learned that you can't make a File\Quit menu item for your XUL application because Firefox has a security protection to prohibit closing a window from code. Of course, you could find some code on the web that crashes Firefox, but there's no telling on how long that code will work before that hole is plugged. In general you might want to try the approach of providing a File\Quit option (unless you're building a control panel or something else) and just have an inline DIV show up that lasts for 6 seconds and says "To quit this application, click the close box on your titlebar."

---

### Post by SuperMike on 2007-01-09
I found that the firewall rule I specified in the article will work, but it's not necessary since my firewall script already has this rule:

iptables -A INPUT -i lo -j ACCEPT

...which permits all 127.0.0.1 (local loopback to itself) activity.

In fact, by using the rule specified in the article above is probably not a good idea because it exposes port 11255 to the outside world, which is not necessary because we only want local connections back to this micro web server (thttpd).

---

### Post by SuperMike on 2007-01-09
If you ever go this route in building your application, one option for building great menus looks like:

[HTML]<html>

<head>

<title>Pure CSS Menus</title>

<style type="text/css">
ul#menubar {
	padding: 0px;
	margin: 0px;
	width: 10em;
	position: relative;
	float: left;
	z-index: 1;
}
ul#menubar a {
	display: block; 
	padding: 0.3em 1em;

	text-decoration: none;

	background: #f7f7f7;

	color: black;

	font-family: Arial,sans;
	font-size: 0.68em;

	cursor: default;
	border: 1px solid #f7f7f7;
}
ul#menubar a:hover {
	background-color: #a0a0a0;
	color: white;
	border: 1px solid #707070;
}
ul#menubar ul li {
	position: relative;
	left: 5px;
}
li#break {

	color: Gainsboro;

	height: 0px;
	background: #f7f7f7;
	border-top: 1px solid Gainsboro;

}
li#menu,li#break,li#popdownmenu {
	list-style-type: none; 
}
li#menu,li#break {
	display: none;
}
ul#menubar:hover > li {

	display: block; 
	border-left: 1px solid Gainsboro;
	border-right: 1px solid Gainsboro;	
}
ul#menubar:hover > li#popdownmenu {
	border-left: 1px solid #f7f7f7;
	border-right: 1px solid #f7f7f7;
	border-bottom: 1px solid Gainsboro;
}
ul#menubar:hover {
	border-bottom: 1px solid Gainsboro;
}
li#popdownmenu,li#popdownmenu:hover {
	cursor:default;
	font-size: 0.68em;
	font-family: Arial,sans;
	background: #f7f7f7;
	padding: 0.35em 0.4em;
	display: block;
	list-style-type: none;
	border-left: 1px solid #f7f7f7;
	border-right: 1px solid #f7f7f7;
}
div#menus {
	width: 100%;
	margin: 3px;
	border-bottom: 1px solid Gainsboro;
	position: absolute;
}
div#body {
	position: fixed;
	display: block;
}
div#toparea {
	position: fixed;
	display: block;
	float: none;
	width: 100%;
	margin: 1px;
	border-bottom: 1px solid Gainsboro;
	background: #f7f7f7;
}
div#bodyarea {
	position: relative;
	display: block;
	float: bottom;
	top: 8px;
	background: white;
	height: auto;
	bottom: 0;
	width: auto;
}
</style>

</head>

<body topmargin=0 leftmargin=0 marginwidth=0 marginheight=0>
<div id="body">
<div id="toparea">
<div id="menus">&nbsp;</div>
<ul id="menubar">
	<li id="popdownmenu">&nbsp;File</li>
	<li id="menu"><a href="?menu=new">New</a></li>
	<li id="menu"><a href="?menu=open">Open...</a></li>

	<li id="menu"><a href="?menu=save">Save</a></li>

	<li id="break"></li>

	<li id="menu"><a href="?menu=quit">Quit</a></li>

</ul>

<ul id="menubar" style="left: -6.9em;">
	<li id="popdownmenu">Edit</li>
	<li id="menu"><a href="?menu=cut">Cut</a></li>

	<li id="menu"><a href="?menu=copy">Copy</a></li>

	<li id="menu"><a href="?menu=paste">Paste</a></li>

	<li id="break"></li>

	<li id="menu"><a href="?menu=selectall">Select All</a></li>

</ul>

<ul id="menubar" style="left: -13.8em;">
	<li id="popdownmenu">Help</li>
	<li id="menu"><a href="?menu=help">Help Contents</a></li>

	<li id="break"></li>

	<li id="menu"><a href="?menu=about">About Menus</a></li>

</ul>
</div>
<div id="bodyarea">
<p>This is a test</p>
<table border=1 cellspacing=1 cellpadding=1 width="100%">
<tr><td>test</td><td>test</td></tr>
<tr><td>test</td><td>test</td></tr>
</table>
<table border=1 cellspacing=1 cellpadding=1 width="100%">
<tr><td>test</td><td>test</td></tr>
<tr><td>test</td><td>test</td></tr>
</table>
</div>
</div>
</body>

</html>[/HTML]

---

### Post by SuperMike on 2007-01-16
I found a way to automatically shut down thttpd when the window is closed.

In the example bash script, after the firefox -chrome line, you could do something like:

```
# find the PID of our thttpd
THTTPDPID="$(ps ax | grep -i 11255 | grep -iv grep | cut -d ' ' -f 1 | tr -d \"\\n\")"
# give the browser some time to load
sleep 2
# go into an endless loop
while true; do
  # take it easy on the processor
  sleep 1
  # if we find our window no longer open, then...
  if (( "$(xwininfo -name 'SQLite Example' 2>&1 | grep -iv 'no window' | wc -l)" == "0" )); then
    # ...kill our thttpd web server
    kill $THTTPDPID
    break
  fi
done
```

But note that this technique breaks the functionality of all the other apps you have hosted on thttpd on this same port number and is not a good idea. That's why I would just opt to leave thttpd open and not use this technique unless you have all your apps on separate port numbers. The thttpd command is smart enough to not reload itself more than once, so you could call this multiple times.

Another route is to implement a SYSV message queue in Bash such that each time an app loads, it updates the message queue with another entry, and when the app unloads, it removes the entry from the message queue. When there are no more entries in the message queue, you could kill the thttpd process on port 11255 (if that's the port you choose to use).

To create a quick and dirty tool in C (even if you don't know C) for interacting with message queues from Bash command line, look at msgtool here:

[http://www.linux.com/guides/lpg/node37.shtml](http://www.linux.com/guides/lpg/node37.shtml)

---

### Post by SuperMike on 2007-01-19
[size="4"]**I Made A Great Discovery Today!!!**[/size]

There is a way to build robust, fast standalone XUL applications without needing a web server like thttpd !

I'll have an example posted here in a day or so as I try to polish it up, but the way it works is:

1. Firefox loads with your chrome XUL file like I've shown above.
2. The XUL should have this extra xmlns line above the existing one we've been using in the example above:

xmlns:html="http://www.w3.org/1999/xhtml"

3. The XUL should remove the IFRAME because it's no longer necessary and should replace it simply with a DIV in XHTML format like so:

<html:div id="mydiv" name="mydiv"></html:div>

4. Your XUL file's <script></script> section should include the initial javascript to display content in "mydiv". It does this like so:

document.getElementById('mydiv').innerHTML = 'put all the HTML for a normal page here';

5. That loads the default HTML content inside 'mydiv'. When someone clicks an element on it, it needs to use normal Javascript onClick="" handlers like so:

<html:input id="MyBtn" name="MyBtn" type="button" onClick="SayHello()" />

6. This will then of course call the ordinary Javascript you already have in the XUL, looking for the function, in this case, SayHello().

7. With normal applications, you're going to want to do things like:

* shell out and run a command, sending the output to a file -- useful for all kinds of things, such as reading and writing to any kind of database, using either Bash, Perl, Python, PHP -- whatever you think you want to require be on the computer for them to run this command. If it were me, I would just stick with Bash and use commands from /usr/bin -- that way you lower the dependencies.

* read the contents of that file and redisplay it in 'mydiv'

* be able to write contents into a file

All of these things are possible using something in XUL called XPCOM and these components are described here:

[http://www.xulplanet.com/references/xpcomref/](http://www.xulplanet.com/references/xpcomref/)

However, **note well** that there's _one more trick_ to getting XPCOM to work in Firefox because _by default it's turned off_. The trick is to add this block of code in the Javascript:

try {
  netscape.security.PrivilegeManager.enablePrivilege("UniversalXPConnect");
} catch (e) {
  alert('This version of Firefox does not support this kind of application. Please upgrade.");
  return;
}

...before running the XPCOM objects. Otherwise, you'll get an error in the ErrorConsole (if you open it up) like so:

**Permission denied to get property UnnamedClass.classes**

The neat thing about XPCOM objects is that there's a pretty decent set of them, giving you the ability to run commands, read/write files, show a file open, save, or print dialog window, read/write remote socket connections, and many other things. Click the XPCOM reference link above to find out what these are and how they are to be called inside the Javascript of your XUL file.

So, to run a command with XPCOM, this example was useful to me:

[http://developer.mozilla.org/en/docs/Code_snippets:Running_applications](http://developer.mozilla.org/en/docs/Code_snippets:Running_applications)

For File I/O, this example was useful:

[http://www.faqts.com/knowledge_base/view.phtml/aid/23360/fid/53](http://www.faqts.com/knowledge_base/view.phtml/aid/23360/fid/53)

[SIZE="4"]**SUMMARY**[/SIZE]

I'll have an example posted in a couple days, but the net of this is that with just one XUL file and firefox, you can build an entire application on Linux as well as make it run super fast. The language you will use is ordinary Javascript with some extra features added in, and perhaps Bash script language or SQL as you need to interact with commands on the system or interact with a database such as SQLite, MySQL, PostgreSQL, or whatever.

To draw the GUI, you use ordinary HTML. With some clever Javascript and CSS, you can make the HTML look and feel like an application GUI like we're used to using. In fact, if the program is only run on Linux, Firefox even has a way to make a rich edit control so that you can do bolding, italics, and so on or provide a way for the end user to do it too.

Instead of doing normal web form submission to a web service, you just call the Javascript in the existing page and keep replacing mydiv's innerHTML value or update the HTML elements inside that DIV.

And these applications can be extremely robust. Take for instance Mozilla Thunderbird -- it is written using XUL, XPCOM, and Javascript. (Er, for the most part -- there is some extra C++ code that it uses via XPCOM.)

Therefore, if you wanted to build a spreadsheet, word processor, Quickbooks Pro for Small Business knockoff, or whatever kind of application or handy utility you wanted, as long as Firefox is installed on the Linux computer, your XUL application could do it all quite nicely, and do it without Python, Perl, PHP, or Java.

And you don't have to keep all your code in one single file. You can have the XUL file call external HTML, Javascript, or CSS files. You can also embed things like Flash, Java applets, or other plugins.

---

### Post by SuperMike on 2007-01-20
[SIZE="4"]**Packaging XUL Apps**[/SIZE]

I just found that if you use this in your Javascript in order to enable XPCOM components:

[INDENT]  netscape.security.PrivilegeManager.enablePrivilege ("UniversalXPConnect");[/INDENT]

...your browser will pop up an UNSAFE warning.

So how do you stop it? Well, unfortunately it means you must use the 'xulrunner' application, which you can download here:

[http://developer.mozilla.org/en/docs/XULRunner](http://developer.mozilla.org/en/docs/XULRunner)
(Look for Linux link.)

This, unfortunately, adds 8.9MB to your application distribution and I wish that Ubuntu would ship with it by default because it's so important for newbies in developing apps. I also wish that you could just do 'apt-get install xulrunner', but I don't have that option.

Okay, so xulrunner can run your XUL application, but it's not that easy yet. You need to do it like so:

1. Create a directory structure like the following, and yes, I know it's crazy:

- application.ini (a text file we will edit in a moment)
- chrome (folder)
[INDENT]- content (folder)[INDENT]- sample (folder)[INDENT]- sample.css (a CSS file for the "skin" of your app)
- sample.js (a javascript file for what you hook up your XUL events to)
- sample.xul (the GUI of the application[/INDENT][/INDENT]
- chrome.manifest (a text file we will edit in a moment)[/INDENT]
- defaults (folder)
[INDENT]- preferences (folder)[INDENT]prefs.js (a special kind of Javascript file we will edit in a moment)[/INDENT][/INDENT]

2. Previously, I have mentioned how you build your sample .xul, .js, and .css files, so I won't go over those again. However, there is a special file you need called application.ini. Edit it so it looks like so:

```
[App]
Name=sample
BuildID=0

[Gecko]
MinVersion=1.5

```

...changing 'sample' above to whatever you want to name your application.

3. Next, find your prefs.js text file that you created and put this into it:

```
pref('toolkit.defaultChromeURI', 'chrome://sample/content/sample.xul');
```

...changing all the 'sample' keywords above to what you want to name your app.

4. Next, find your chrome.manifest text file that you created and put this into it:

```
content sample file:content/sample/
```

...changing all the 'sample' keywords above to what you want to name your app.

5. In your XUL file, you'll need a different way to address your Javascript. Do it like this right after your last xmlns line, starting a new line:

```
<html:script src='chrome://sample/content/sample.js' />
```

...changing all the 'sample' keywords above to what you want to name your app.

6. In your XUL file, to load the CSS, I think I learned that you don't need a path to it. I load my CSS like so:

```
<?xml-stylesheet href="sample.css" type="text/css"?>
```

...right after the line about global skin and right before the window tag.

7. So, with all this preparation done, you need to download and install your XUL Runner app. I just uncompress it into /usr/share as /usr/share/xulrunner and then do this:

```
$ sudo  ln  -s  /usr/share/xulrunner  /usr/bin/xulrunner
```

8. And now, FINALLY (phew!), to call for instance a 'sample' folder that contains my app, which I might have placed inside /usr/share as /usr/share/sample, I would call it like so:

```
$ xulrunner  /usr/share/sample/application.ini
```

...and up pops your window for your application. Moreover, when you do something that activates your Javascript and if that Javascript calls an XPCOM object, it will no longer prompt you about things being unsafe or not. It will just run.

[INDENT][I]Commentary: I guess I can fault the Mozilla devs who came up with this crazy way to call an XUL app through xulrunner. If it were me, I would just prefer to throw everything into one directory and call it with 'xulrunner <directory>/sample.xul', but this is the way it is.
[/I][/INDENT]

So, now that you know this, here's some more advice. There's a tool you can find on the web called 'makeself' that can combine all of this into one Linux executable and have it call your Bash script. The only thing it doesn't come with is 'xulrunner'. Now, if you prefer to bundle your app with 'xulrunner', and you have read the license agreement for it and are in compliance, then you can use makeself to throw everything together including xulrunner. This could potentially make your application somewhere between 9MB and 15MB, but I guess that's not too bad -- I've seen worse. And, if distros of Linux start to ship with the 8.9MB xulrunner, or if it's easily available on 'apt', then you can reduce your application's size by that much.

---

### Post by SuperMike on 2007-01-27
[SIZE="4"]**Hosted Sample**[/SIZE]

I have decided to build a great example of standalone XUL applications for Ubuntu Linux (and other Linuxes) at Google Code's new Hosted Projects site.

You can go to this page here:

**[COLOR="DarkOrange"]_[http://code.google.com/p/simplexul/]("http://code.google.com/p/simplexul/")_[/COLOR]**

The download there permits you to rapidly build standalone, simple-to-powerful Ubuntu Linux applications with nothing more than HTML and Javascript knowledge, and you can also build client/server applications too.

---

### Post by airtonix on 2007-05-14
you are superrrrrrrmiiiiiiike......i canna bend space anna time.

lol seriously though...this process you describe is where i was on windows about ten years ago.....its awesome. it was soooo ahead of its time and the damn microsoft management canned it.

It was aslo the time when this XUL was being forumlated...but now you've given me hope again....

could we make things like : 

 + web desktop ( gnome-active-desktop)?
 + custome konfabulator type widgets?
 + virtual layers for each virtual desktop? like osx does for its widgets.


edit :  oooo [[jumps for joy]] we can use mootools now too... wooohoo

reality-check : i hope it doesnt consume too much cpu or ram for low-end machines like 500mhz 256mb ram type setups.
if so then maybe there is a way through the use of XML, XSLT, to convert it into a ncurses interface descripta?

---

### Post by SuperMike on 2007-05-15
Glad you can actually comprehend this complexity and appreciate what I have figured out. Not many people have noticed how cool this is.

Answers to your questions:

web desktop: is a pretty heavy solution for that, no, not a good match
konfabulator: don't know what that is
osx widgets: again, not the best match for that kind of solution -- for that you need something designed in C or C++ that displays windows super fast, with low memory consumption, and acts just like the OS X widgets

The best solution for these XUL apps are for building rich client (mostly Linux) apps like you might use VB6 on Windows, for instance. Also, if you're clever, you can even make the app check the web server for more recent code and download an updated version before running.

You could even make a knockoff Quickbooks for Small Business clone with this, should you feel so benevolent.

---

### Post by marianom on 2007-07-29
Hi Mike, cool how to and very enthusiastic intro to the XUL world. Congratulations. I totally share your thoughts.

In case I missed it in your posts let me tell you that you can grab xulrunner directly from repos in Feisty. 
I started learning XUL and coupling it with pyXPCOM (to save me the C++ amenities) since a few weeks ago and so far I'm happy with it (It seems that the Ubuntu's xulrunner does not come with pyXPCOM included so I'll have to build it from source).

---

### Post by SuperMike on 2007-09-02
Word to all, now that time has passed.

Making XUL apps is fairly easy once you know the steps. You can probably have less frustration with it than with PyGTK and Python. The downside? Well, it's slow and sucks memory. Every time you fire up xulrunner, even though it's smaller than a full blown browser, in a sense it's like opening a web browser every time you open one of these XUL apps. Sure, you can knock out stuff fast, but you're going to need a decent workstation to make these things pop on the screen fairly fast.

If you want something faster, it appears that Python and PyGTK is still the way to go. It's how Gnome implements some (but not all) control panels and how many apps are built these days.

Maybe some day someone will make either a faster xulrunner or come up with a new platform. Let's hope that new platform uses Javascript since everyone who does web dev already knows it and since it can be a beautiful language at times when you rip out the cross-platform browser junk out. BTW, if you haven't checked out ngs-js, I suggest you give it a try. It has a lot of potential.

---

### Post by bsilver6 on 2012-03-08
I would like to post some current info on XUL app development, having just jumped through the hoops and scoured the Mozilla site for hours just get a Hello World app working.

Firstly, you can now bootstrap your XUL app with Firefox (since version 3). So you don't need to require XULRunner. Recent versions of firefox come with their own internal XUL runtime, which you can access with the -app commandline switch (you don't use -chrome anymore).

e.g.
```
firefox -app path/to/application.ini -jsconsole
```

The structure of a XUL app is much the same as SuperMike has described, with one important exception -- the "chrome.manifest" must now be in the **root** of the app directory. So Mike's example might now contain the manifest file:
```
content sample chrome/content/sample
```

Another option is to have 2 chrome.manifest files, one in the app root, containing:
```
manifest chrome/chrome.manifest
```
And the other in the chrome directory containing:
```
content sample content/sample
```

This is a way of making a single root manifest point to as many other manifests as you like, giving you more control of the directory structure.
But as Mike says, its still crazy.

There are a lot of silly hoops to jump through to get started with XUL, and the documentation is patchy, but it really is a great technology and very beginner friendly once you figure out the boilerplate stuff. I should mention that the APIs themselves are actually well documented at the [Mozilla Developer Network]("http://developer.mozilla.org").
And the ability to implement as much of your application in HTML as you like is all the more attractive with the current advent of HTML5.

---


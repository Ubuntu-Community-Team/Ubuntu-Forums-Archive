---
title: "Dynamically Generated Server Status page"
date: 2008-10-21
forum: Server Platforms
---

### Post by chejrw on 2008-10-21
Hey everyone.

I run a small file- and web-server machine that's running Ubuntu 7.10 (I initially used it as a workstation, and then installed the LAMP package and disconnected it's monitor).

I would like to have a server status web page that's dynamically generated when a user loads it - something that shows the current free space on each of the hard disks (there are 2), current CPU load, current network utilization, that sort of thing.

Does anyone know if there is any not-too-complicated way to do this?

---

### Post by EvilMarshmallow on 2008-10-21
You could use the LAMP to do it like this:

[LIST=1]
[*]Set up a database with a table that has all the points you want to check
[*]For each data point, write a script that puts a value in the database.  Put it in cron at the frequency you desire.
[*]Make a simple web page in php/perl/etc. that reads the value from the database
[/LIST]

The benefit of doing it this way is you build a history.  You can create a page with the right widgets that has a graph to show the memory use/network use over the last few days.

It probably isn't particularly easy to set up.  Each script will have to have its own way of doing things.  The good news is that adding new features to your system will be as simple as creating a new column, writing a new script to put data in it, and adding the results to your php page.

---

### Post by huwnet on 2008-10-21
phpsysinfo will probaly do what you want :)
[http://phpsysinfo.sourceforge.net/](http://phpsysinfo.sourceforge.net/)

You can also look into Cacti

---

### Post by iponeverything on 2008-10-21
:) or just install webmin

It has good default system status page.

---

### Post by MJN on 2008-10-21
> **chejrw said:**
> Does anyone know if there is any not-too-complicated way to do this?Whilst the suggestions given are all valid I think an easy, yet flexible/powerful, way would be to use [Server Side Includes]("http://httpd.apache.org/docs/2.0/mod/mod_include.html") (SSI).
 
Specifically, you can instruct Apache through HTML to execute commands/script and display the output. As an example, take a look at the bottom of all my pages at [www.newtonnet.co.uk]("http://www.newtonnet.co.uk") - each page includes the current time/date and load stats - this is created dynamically each time the page loads using the 'date' and 'uptime' commands. The top of each page also says when it was last modified (without me having to manually update it). You can of course get as creative as you like and use customised scripts to obtain whatever info you might desire.
 
To implement SSI you can get the ball rolling with the minimum of effort - 
 
1. For a given **<Directory>** container in your Apache config ensure SSI is enabled by adding **Includes **to the **Options **directive. You also need to tell Apache what files should be parsed for SSIs, for this I use the **XBitHack On** directive which says any file with the user-execute flag set can use SSI (see [here]("http://httpd.apache.org/docs/2.0/mod/mod_include.html#xbithack") for further details)
2. Set the user-execute flag on the file(s) you want SSI to work on (e.g. **chmod u+x myfile.htm**)
3. Add the necessary HTML code to your page(s) as required. For example:
 
To output the current time: **<!--#exec cmd="date" -->**
To output the free disk space:** <!--#exec cmd="df -h" -->**
To output the last modified page date: **<!--#echo var="LAST_MODIFIED"-->**
To include the contents of another file (e.g. to have a common header/footer for each page): **<!--#include virtual="/someotherfile.htm" -->**

There are all sorts of 'stock' commands like the above, but of course given you can write your own scripts to find/manipulate date the only limitation is your imagination!
 
That's a 2-minute run through so if you want me to provide detail on any specifics just shout.
 
Mathew

---

### Post by chejrw on 2008-10-21
Thanks MJN, that's just the sort of thing I had in mind.  Both webmin and phpsysinfo would put way more information out there than I think is necessary.

I had also thought of just creating a cron job that runs a few commands and outputs them to a file every once in a while, but I'd rather something dynamic so that it's always up-to-date, but doesn't eat unnecessary resources running all the time.

The SSI stuff seems fairly straightforward, I'll read a little more about it.  If I have any issues, I'll give you a shout.

---


---
title: "Running R statistics in a PostgreSQL database"
date: 2007-11-14
forum: Server Platforms
---

### Post by Garyu on 2007-11-14
There is a neat little thing called PL/R that you can use to access R statistical functions from an PostgreSQL database.

sudo aptitude install postgresql-8.2-plr

Then, either in your template1 to make it default for all databases, or in the database you want to use PL/R in:
```

CREATE FUNCTION plr_call_handler()
RETURNS LANGUAGE_HANDLER
AS '$libdir/plr' LANGUAGE C;

CREATE LANGUAGE plr HANDLER plr_call_handler;
```

Now you should have PL/R working. For code examples, look at
[http://joeconway.com/plr/](http://joeconway.com/plr/)
You really need to know some R code to make it work well.


[http://www.varlena.com/GeneralBits/Tidbits/bernier/art_66/graphingWithR.html](http://www.varlena.com/GeneralBits/Tidbits/bernier/art_66/graphingWithR.html)
This page has a short tutorial on how to use PL/R to create graphs of firewall hits and so forth. Unfortunately, in Ubuntu it doesn't work. 

It seems, PL/R requires the X server for displaying data. That does not work in Ubuntu at least. So you have to use a fake X server to go around this problem:

sudo aptitude install xvfb

gksudo gedit /etc/postgresql/8.2/main/environment
```
DISPLAY = ':5.0'
R_HOME = '/usr/lib/R'
```

/usr/X11R6/bin/Xvfb :5 -screen 0 1024x768x16 >& /dev/null &
(maybe this should be run as postgres user- sudo su postgres - or even put in the .bash_profile of postgres user)

sudo /etc/init.d/postgresql-8.2 restart
(to restart postgresql, or you may have to reboot the computer)

Now you will be able to create graphs like this:
```
CREATE OR REPLACE FUNCTION test_graph() RETURNS text AS
'
X11(display='':5'');
png(''test_graph.png'');
plot(rnorm(50), rnorm(50));
dev.off();
print(''done'');
'
LANGUAGE plr;
```


**IMPORTANT NOTE:**
If you give an absolute path to save the image, you will get an error:
```
# select test_graph();
ERROR:  R interpreter expression evaluation error
DETAIL:  Error in X11(paste("png::", filename, sep = ""), width, height, pointsize,  : 
        unable to start device PNG
CONTEXT:  In PL/R function test_graph
```

So you can specify a file name, but not a path. All of the images will be saved in this folder:
/var/lib/postgresql/8.2/main/
So you will have to write a script to copy the graphs if you want them in any other place.

EDIT: You can use any path to where the user postgres has rights. Easiest way of doing this is to use /tmp
All of the PNG's are owned by user postgres, so you have to chown and chmod them before using.

---

### Post by meatpan on 2007-11-14
Sounds like a great tool!  Just curious, do you have png support in your ubuntu install?  'dpkg -l | grep png' should tell you.

Edit: Forgot to mention that the science/education forum has a lot of R users, they might be able to help you if this post doesn't work out.

---

### Post by Garyu on 2007-11-15
> **meatpan said:**
> Sounds like a great tool!  Just curious, do you have png support in your ubuntu install?  'dpkg -l | grep png' should tell you.

Yes. As I said, the problem is related to PL/R trying to use the X server to generate the picture. I am sure of this.

[http://72.14.253.104/search?q=cache:8thECJYzSi0J:gborg.postgresql.org/pipermail/plr-general/2004-November.txt+pl/r+xvfb&hl=en&ct=clnk&cd=3&gl=us&client=firefox-a](http://72.14.253.104/search?q=cache:8thECJYzSi0J:gborg.postgresql.org/pipermail/plr-general/2004-November.txt+pl/r+xvfb&hl=en&ct=clnk&cd=3&gl=us&client=firefox-a)
Found this discussion from 2004 and tried adding to my code:
X11(display='':5'');
But I still get the same error as before.

If you're curious, this is the code I am testing with:
```
CREATE OR REPLACE FUNCTION test_graph() RETURNS text AS
'
mytest <<- pg.spi.exec(''select lanid as "ID" from lan'');
X11(display='':5'');
png(''/home/dan-erik/exjobb/test_graph.png'');
plot(mytest,main="Graphics Demonstration");
dev.off();
print(''done'');
'
LANGUAGE plr;

```

I also tried this:
```
$ DISPLAY=:5.0 xeyes
Xlib: connection to ":5.0" refused by server
Xlib: No protocol specified

```
Not sure what that means though. Could it be that Xvfb is incorrectly configured?

---

### Post by Garyu on 2007-11-15
Found a solution. One has to edit a config file and never use absolute paths.

Edited the main post to include the fix, so now this has turned from a question into a howto. :cool:

---

### Post by meatpan on 2007-11-15
Yeah, thanks for posting the solution.  That was a relatively obscure config requirement.  I'm planning on trying this postres/R package using the notes from this thread.

---

### Post by Rodriel on 2008-06-04
You can use absolute paths if you are sneaky about it. I got it to work by doing the following:

filename <- paste("", "home","rodriel","test_graph.png", sep="/");
png(filename);

Make sure that the postgres user has write permissions in whatever directory you are writing to as well.

Thanks for all the help this thread was very useful.

---

### Post by Rodriel on 2008-06-05
Played around a bit more with this because I wanted to output my graphs to a Web browser. I got it to work by making the following modifications to the above code:

First I changed the depth to be 24 bits instead of 16 in Xvfb
```

/usr/X11R6/bin/Xvfb :5 -screen 0 1024x768x16 >& /dev/null &
```

becomes

```

/usr/X11R6/bin/Xvfb :5 -screen 0 1024x768x24 >& /dev/null &
```

Ensure that my display is set correctly
```

export DISPLAY=':5'
```

Next, I installed the cairoDevice and RGtk2 packages
```

apt-get install r-cran-cairodevice r-cran-rgtk2 
```

Now open up your postgresql database and create a function such as this.
```

CREATE OR REPLACE FUNCTION plr_plot_return_data() RETURNS TEXT AS
'
mytest <<- pg.spi.exec(''select year as Year, strikes as Strikes from stats'');
library(cairoDevice)
library(RGtk2)
pixmap <- gdkPixmapNew(w=500, h=500, depth=24)
gdkDrawableSetColormap(pixmap, gdkColormapGetSystem())
asCairoDevice(pixmap)
plot(mytest,col="red",type="l")
plot_pixbuf <- gdkPixbufGetFromDrawable(pixmap, pixmap$getColormap(), 0, 0, 0, 0, 500, 500)
buffer <- gdkPixbufSaveToBufferv(plot_pixbuf, "png", character(0), character(0))$buffer
finalpng <- paste(buffer, collapse="")
return(finalpng)
'
LANGUAGE plr;
```

Lets see if it worked or not. If it worked you should see a long string of hex digits.
```

select plr_plot_return_data();
```

If it didn't work, it means either your SQL statement is wrong, that the $DISPLAY variable you exported does not match that of the Xvfb, or that you did not install cairoDevice or RGtk2 properly. Verify that all of these work.

Now its time for the Web part. I chose PHP because its quick and easy. You will need to ensure that the postgres user has a password. You can do this with the following command:

```

ALTER USER postgres WITH PASSWORD 'testing';
```

Also ensure you have PHP installed as well as the php5-pgsql package. Now for the PHP file
```

<?php
$dbconn = pg_connect("host=localhost port=5432 dbname=somedb user=postgres password=testing");
$rs = pg_query( $dbconn, "select plr_plot_return_data();" );
$hexpic = pg_fetch_array($rs);
$cleandata = trim($hexpic[0], "{}");
$final = pack("H*", $cleandata);
header("Content-Type: image/png");
header("Last-Modified: " . date("r", filectime($_SERVER['SCRIPT_FILENAME'])));
header("Content-Length: " . strlen($final));
echo $final;
?>
```

You should see your graph if you hit the php file in a Web browser now.

Cheers!

---


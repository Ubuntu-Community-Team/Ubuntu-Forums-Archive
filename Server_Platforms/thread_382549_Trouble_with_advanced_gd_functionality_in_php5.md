---
title: "Trouble with advanced gd functionality in php5"
date: 2007-03-12
forum: Server Platforms
---

### Post by aethreyes on 2007-03-12
I'm trying to dynamically create an image using gd functions in php5.  Most of the gd functionality works fine, but when I try to use the following functions I get a "**Fatal error:** Call to undefined function"

```

imageconvolution()
imagefilter()
```

Most of what I know about gd functions I've read on the php.net site: [http://au.php.net/gd]("http://au.php.net/gd")

The pages for the above functions contain a note stating:

> **Note:** This function is only available if php is compiled with the bundled version of the GD library.

Now, I'm running a 6.06 LAMP server that has been **apt-get updated** and **upgraded**, my phpInfo() says that I'm running **php v5.1.2**, and my gd version lists as "**2.0 or higher**".  I installed gd by running **apt-get install php5-gd**, but I'm not sure this is the right way to go about it.  I've uncommented the gd.so line in my php.ini but it didn't address the problem.  I also restarted apache2 at several stages of the process and subsequently restarted my whole box with no improvement in the situation.

I've been searchin the web for a few hours to find a solution to my problem, and it seems that if you compile php5 using the --with-gd option, that the phpinfo() entry for gd version reads "bundled 2.0" or something, which I'm assuming is what I need (as the gd that comes bundled with php has been developed independently and has functions that don't come with the standalone version).

Has anyone had any experience with this, or had any luck getting these functions working?  Is there a way to configure php5 --with-gd using apt-get so I don't have to resort to compiling from source?  Any help would be most appreciated.

---

### Post by dryliketoast on 2008-01-03
bump - I am also interested to know the answer to this problem

---

### Post by ericson578 on 2008-05-02
I installed php5-gd through the synaptic package manager, then reloaded apache and everything worked fine.

My problem was this line in a php script that was crashing with no error message at all:
$im = @imagecreatefromjpeg($path);

Installing the above package completely fixed it for me.  Unfortunately it took me forever to figure out where the problem was occurring, thanks php for just crashing and not outputting any errors at all!

---

### Post by hmida on 2008-05-03
It's because you put @ before your function, if you put just imagecreatefromjpeg(blabla) you will have your error.

aethreyes : If you always have this problem why not check this link : [Here :)]("http://blog.madtech.cx/2006/12/08/debian-etch-libapache2-mod-php5-with-bundled-libgd-gdlib/")

---


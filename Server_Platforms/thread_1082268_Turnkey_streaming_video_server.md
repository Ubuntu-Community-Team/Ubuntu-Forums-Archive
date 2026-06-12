---
title: "Turnkey streaming video server"
date: 2009-02-27
forum: Server Platforms
---

### Post by gdselzer on 2009-02-27
I wasn’t sure whether to post this in the Multimedia Forum or here.  In the end, I figured the geeks in the Server forum would be all over this…

I am trying to setup a way for the grandparents to easily view the (many) videos we have started taking of the rugrats now that we have upgraded to a digital camera that takes halfway decent videos.  I already have a website I use to share pictures with them hosted on a box in the basement over DSL. (Ubuntu 8.04 Server, Apache 2, JAlbum used to create webalbums of the pics)  I’ve been looking around for a good solution on the internets and haven’t found what I’m looking for.  

My DREAM scenario is an easy to install (aptitude?) and configure app that works like this:  My wife figures out which videos she wants to share.  She takes the .mov files directly from the camera and copies them into a shared folder on the network.  The dream app then does whatever converting, coding, building, etc. it needs to update a YouTube style webpage on my box that allows the grandparents to easily view all the videos of their precious grandchildren they want.

I understand that this dream app may not exist, so any guidance you folks can provide as to how I get to this end result would be great appreciated.

Most important aspects to this project are:
1.	It be easy for the wife to use.  Ideally she will not be required to convert videos, rewrite web pages, etc.  I’d like for her to be able to drag and drop the videos into a shared directory and have the “system” take care of everything else.
2.	It needs to be easy for the grandparents to use.  They can navigate to our webpage and click on things.  Much more and we start having problems.
3.	Minimal intervention by me after everything is up and running.

Thanks for the help.

---

### Post by phudgee on 2009-02-27
Couldnt you just write a bash script to do the following:

- run ffmpeg on every file in the particular directory
- move them to the hosted directory. 


Have her put the files in the directory and run the script.

Then on your webserver, use PHP to build a dynamic list of files in the video directory, and display them on the page.

You could even write your bash script to email the grandparents whenever she adds new videos.

If she didnt want to run the script after uploading the videos, you could just add a cron job to check it daily or something.

---

### Post by gdselzer on 2009-02-27
Sounds good to me.  However...while I've played around with bash and PHP scripts here and there, I am way out of my league taking on a project like this.  I wouldn't even know where to begin.  Any advice on scripts that you've seen that do similar tasks that I could use as a base?  I'm open to stumbling my way through this, but would prefer to find something pre-canned.

---

### Post by phudgee on 2009-02-27
Im talking a simple bash script, as I too am green on complex one.

I'd first manually convert a few files with ffmpeg, and get down the command line switches that work best for the types of files you want...

This is by no way a complete script, but should give you an idea.

Say the directory your wife moves the files into is /home/wifey/videos

and the folder on the webserver is /var/www/videos

You could do something like this:

```
#!/bin/bash
cd /home/wifey/videos
for file in `dir -d *` ; do
ORGNAME=`basename $file .mpg` # or .mov or whatever the original file format is
NEWNAME=${ORGNAME}.flv
ffmpeg -i $file -deinterlace -ar 44100 -r 25 -qmin 3 -qmax 6 $NEWNAME
done
mv *.flv /var/www/video
```


some of my syntax might be off in that, but it's a good starting ground.


in /var/www/videos  create index.php and in it put something like this:

```
      <?
          $path = "/var/www/videos/";
          $dir_handle = @opendir($path) or die("Error opening $path");
          while ($file = readdir($dir_handle)) {
            if($file == "." || $file == ".." || $file == "index.php" ) { continue; }
            echo "<a href=\"$file\">$file</a><br />";
          }
          closedir($dir_handle);
      ?>

```


assuming your original files are named video1.mpg, video2.mpg, etc..

the out put at [http://www.yourserver.com/videos](http://www.yourserver.com/videos)  would be:

[video1.flv]("http://www.server.com")
[video2.flv]("http://www.server.com")
[video3.flv]("http://www.server.com")
etc...



hope that makes sense.... i tend to ramble...

---

### Post by gdselzer on 2009-02-27
It does (mostly) make sense.  Thanks!  

Do I understand correctly that the final result would be a webpage that is a list of filenames?  When Grandma clicks on one of the file names, will the entire file have to download before she can watch it or will it "stream"?

---

### Post by phudgee on 2009-02-27
You are correct on the webpage output.

You could change it to <EMBED> them in a player, so that it could buffer while it plays.

I think they way I have it that it will in fact have to download the whole file prior to playing.

---

### Post by gdselzer on 2009-02-27
I was hoping to have it stream as well.  Any thoughts on solving that part?

---

### Post by phudgee on 2009-02-27
Heres a free opensource player:

[http://www.longtailvideo.com/players/jw-flv-player/](http://www.longtailvideo.com/players/jw-flv-player/)

It looks like you have to upload two files, and per their website, use the following code to embed the videos into the player:


```

<p id='preview'>The player will show in this paragraph</p>

<script type='text/javascript' src='swfobject.js'></script>
<script type='text/javascript'>
var s1 = new SWFObject('player.swf','player','400','300','9');
s1.addParam('allowfullscreen','true');
s1.addParam('allowscriptaccess','always');
s1.addParam('flashvars','file=video.flv');
s1.write('preview');
</script>
```

So then rather than just a list of filenames, it would be a long page of videos (like youtube) and you can click the video to play it.


Also, you will want to exclude these two files from your PHP loop, like . and .. and index.php are

---

### Post by jimberry on 2011-10-02
I know this is an old thread, but someone may still find it while searching for an answer to a similar problem. :)

The jAlbum application mentioned in the opening post is actually an ideal solution.

You can create an index page of thumbnails which link directly to the videos.
 
You can set up the program to run in server mode, looking for updated files and updating the indexes when required.

This seems to answer all 3 requirements sought by the original poster.

There is also a well supported community forum where requests for assistance are often answered on a same day basis (indeed, same hour is not uncommon). 
[http://jalbum.net/forum/index.jspa?categoryID=1](http://jalbum.net/forum/index.jspa?categoryID=1)

---

### Post by stoute on 2011-10-02
You could make the entire process easier on the end user by creating a main home page with multiple pages for each embeded video. like Netflix.

---

### Post by kleverbear on 2011-10-03
> **jimberry said:**
> I know this is an old thread, but someone may still find it while searching for an answer to a similar problem. :)

The jAlbum application mentioned in the opening post is actually an ideal solution.

You can create an index page of thumbnails which link directly to the videos.
 
You can set up the program to run in server mode, looking for updated files and updating the indexes when required.

This seems to answer all 3 requirements sought by the original poster.

There is also a well supported community forum where requests for assistance are often answered on a same day basis (indeed, same hour is not uncommon). 
[http://jalbum.net/forum/index.jspa?categoryID=1](http://jalbum.net/forum/index.jspa?categoryID=1)

I agree, good thread to setting up a quick web based streaming solution.

---


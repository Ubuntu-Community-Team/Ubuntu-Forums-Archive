---
title: "Howto: Movie covers as video thumbnails (hack) (it works for books too)"
date: 2008-02-24
forum: Tutorials
---

### Post by Yuzem on 2008-02-24
**Description**
This is a video thumbnailer that searches imdb for covers based on the file names.
It works for movies in the specified paths (recursively).
For the rest of the cases or if no cover is found the default thumbnailer is used.

Screenshot:
[[IMG]http://img227.imageshack.us/img227/4005/thumbnailfactorynf1.th.png[/IMG]](http://img227.imageshack.us/my.php?image=thumbnailfactorynf1.png)

**Installation**
Now there is a deb package.
Download and install:
[**[COLOR="Red"]Download (gnomefiles)[/COLOR]**]("http://gnomefiles.org/content/show.php/imdb-thumbnailer?content=132112")

[COLOR="Red"]You can access the rest of the instructions with the following command[/COLOR]:
	```
imdb-thumbnailer --help
```

**Set the thumbnailer**
	For nautilus:
		```
imdb-thumbnailer --set-nautilus
```

	For thunar:
		```
imdb-thumbnailer --set-thunar
```

**Preferences**
```
gedit ~/.imdb-thumbnailer/config
```
Add there the paths to your films like this:
```
films_path[1]=/home/user/Films
films_path[2]=/home/user/trailers
```
Don't forget to set a different number for every path.

**Options**

[INDENT]**Set a custom cover:**[/INDENT]
```
imdb-thumbnailer --set video1 cover1 video2 cover2 etc...
```

[INDENT]**Remove thumbnails:**[/INDENT]
If your movies already have thumbnails you can remove them with:
```
imdb-thumbnailer --remove video1 video2 etc...
```

[INDENT]**Update thumbnails:**[/INDENT]
Force the filebrowser to rebuild the thumbnails for the specified videos by changing their modification time 1 second:
```
imdb-thumbnailer --update video1 video2 etc...
```

**Uninstall**
```
sudo rm /usr/bin/imdb-thumbnailer
```

---

### Post by electricshoes on 2008-03-05
This is really cool. Thanks for the Howto!!

---

### Post by Yuzem on 2008-08-10
There is a new version.
Now it is much better and is no longer a hack.

[**[COLOR="Red"]Download[/COLOR]**]("http://www.gnomefiles.org/app.php/imdb-thumbnailer")

---

### Post by Bou on 2008-08-12
Is there any chance to talk to Elisa developers and turn this into an Elisa plugin? That would be great.

---

### Post by Yuzem on 2008-08-12
I would like to help if I can but I am not a real programmer. I can only write in bash.

I don't think Elisa's devs want bash code and the imagemagick dependency but if somehow I can help I would like to.

The code to get the cover from a given name is very simple:
```
#!/bin/bash

read -p "Tile of the movie: " input

search_term=$(echo "${input##*/}" | sed -e 's/[cC][dD][1-9]//' -e 's/[\(][1-9][oO][fF][1-9][\)]//' -e 's/[1-9][oO][fF][1-9]//' -e 's/[_-\.]/ /g' -e 's\....$\\' -e 's/ /+/g' -e 's/(/%28/g' -e 's/)/%29/g')
movie_cover=$(wget -U firefox -qO - "http://www.google.com/search?hl=en&q=site%3Aimdb.com%2Ftitle+${search_term}&btnI=I%27m+Feeling+Lucky&meta=" | grep -A1 -i '<div class="photo">' | sed -n "2 p" | sed "s|.*src=||" | cut -d\" -f2)

echo "$movie_cover"
```

When executed it will ask for the movie title and it should return the cover url.

---

### Post by ahC8shio on 2008-08-13
This is a little off-topic but I&#8217;d love to know what GTK theme was Yuzem using in the screenshot.

---

### Post by Yuzem on 2008-08-13
The compiz/beryl theme is cerebro.

The gtk theme is orion for the aurora engine:
[http://www.gnome-look.org/content/show.php/Orion(aurora)?content=71909](http://www.gnome-look.org/content/show.php/Orion(aurora)?content=71909)

---

### Post by Yuzem on 2008-08-22
New version:
[**[COLOR="Red"]Download[/COLOR]**]("http://www.gnomefiles.org/app.php/imdb-thumbnailer")

---

### Post by mcbean on 2008-08-23
This looks awesome, thanks for this. But for some reason it's only fetching a few covers. I'm fairly certain I'm doing something wrong! Any thoughts ? 

I put the films_path in the config file and tried just running $imdb-thumbnailer --update. However it only fetched the 1st 3 covers then stopped. 

I also tried: 
$ imdb-thumbnailer --update /media/hd/Videos/*
ERROR:"/media/hd/Videos/Blood Diamond" does not exist

Blood Diamond is in it's own folder... I tried with -r and -R, but that makes no difference. 

Any help would be much appreciated!

---

### Post by Yuzem on 2008-08-23
I think that it doesn't behave with the asterisk if the files have spaces.

Try this:
```
imdb-thumbnailer --update drag_and_drop_here
```

Don't type 'drag_and_drop_here' just drag all the videos from the filemanager and drop them there.

Does it work now?
I will try to fix the asterisk problem in the next version.

---

### Post by mcbean on 2008-08-23
Amazing! Thanks. That works great.

---

### Post by Voorhees1979 on 2008-08-30
I am having some issues with this. I have installed the latest deb package. When I type:

gedit ~/.imdb-thumbnailer/config

It opens up with a blank screen, cant save to it as the file doesnt exist.

Any ideas??

Thanks

---

### Post by Yuzem on 2008-08-30
Yes:
```
touch ~/.imdb-thumbnailer/config
gedit ~/.imdb-thumbnailer/config
```

And add your paths there as explained in the help page:
```
imdb-thumbnailer --help
```

---

### Post by Voorhees1979 on 2008-08-30
Hi

I did try that

voorhees@voorhees:~$ touch ~/.imdb-thumbnailer/config
touch: cannot touch `/home/voorhees/.imdb-thumbnailer/config': No such file or directory

Many Thanks

---

### Post by Yuzem on 2008-08-30
mmm... I think I know what the problem is, try this:
```
mkdir ~/.imdb-thumbnailer
touch ~/.imdb-thumbnailer/config
gedit ~/.imdb-thumbnailer/config
```

---

### Post by Voorhees1979 on 2008-08-31
Thats it. Works fantastic now. Many thanks. This is a must have app.

Thanks again

---

### Post by Bou on 2008-09-13
I proposed it to be included in ubuntu and used by default: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/269803](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/269803)

---

### Post by jesterthejedi on 2008-09-13
download link is bad, found it on softpedia:
[http://linux.softpedia.com/get/Desktop-Environment/Gnome/imdb-thumbnailer-40381.shtml](http://linux.softpedia.com/get/Desktop-Environment/Gnome/imdb-thumbnailer-40381.shtml)

---

### Post by tacka on 2008-11-30
hi,

i`m just wondering how to get shadow under covers? is it possible?

thx for help

---

### Post by Yuzem on 2008-11-30
Yes, it is possible but it doesn't work well on nautilus. It seems that it doesn't detect transparencies in thumbnails.

Do this at the terminal:
```
gedit ~/.imdb-thumbnailer/config
```

and add:
```
theme_name=shadow
```

New thumbnails will get the shadow theme.

---

### Post by tacka on 2008-11-30
> **Yuzem said:**
> Yes, it is possible but it doesn't work well on nautilus. It seems that it doesn't detect transparencies in thumbnails.

Do this at the terminal:
```
gedit ~/.imdb-thumbnailer/config
```

and add:
```
theme_name=shadow
```

New thumbnails will get the shadow theme.

thx it`s looking great now :) 

[IMG]http://www.imagecross.com/04/image-hosting-view-11.php?id=8666zrzut_ekranu-filmy---Przegl-darka-plik-w.png[/IMG]

[http://www.imagecross.com/04/image-hosting-view-11.php?id=8666zrzut_ekranu-filmy---Przegl-darka-plik-w.png](http://www.imagecross.com/04/image-hosting-view-11.php?id=8666zrzut_ekranu-filmy---Przegl-darka-plik-w.png)

---

### Post by Yuzem on 2008-11-30
You are welcome and is good to know that the transparency problem is fixed on Intrepid. :)

---

### Post by Psyphre on 2008-12-03
This is absolutely fantastic. My thanks to whoever made and contributed to this fantastic script!

I was wondering if this also works for folders?
It works perfectly for normal video files which is fine for movies, but not so much for TV shows. For example I have a battlestar galactica folder which has all the episodes. Is there a way that I can set the folder to have a thumbnail?

In Gutsy I used to be able to just drag an image to set as its folder icon, but for whatever reason in hardy they have removed the border around a thumbnail when its set as an icon. :(

---

### Post by Yuzem on 2008-12-03
> **Psyphre said:**
> This is absolutely fantastic. My thanks to whoever made and contributed to this fantastic script!

You are welcome. :p
> **Psyphre said:**
> 
I was wondering if this also works for folders?
It works perfectly for normal video files which is fine for movies, but not so much for TV shows. For example I have a battlestar galactica folder which has all the episodes. Is there a way that I can set the folder to have a thumbnail?
I think that there are no file manager that allow thumbnails for folders.
You could try [avatar-factory]("http://ubuntuforums.org/showthread.php?t=486359") that does something similar.

> **Psyphre said:**
> 
In Gutsy I used to be able to just drag an image to set as its folder icon, but for whatever reason in hardy they have removed the border around a thumbnail when its set as an icon. :(
That is very strange, normally, the image should be moved or copied to the destination folder.

---

### Post by Yuzem on 2008-12-04
I have posted an idea on ubuntu brainstorm that is related to this application. If you like it you can vote for it. [Here it is]("http://brainstorm.ubuntu.com/idea/16240/").

[[IMG]http://img230.imageshack.us/img230/5808/pantallazohu0.th.jpg[/IMG]](http://img230.imageshack.us/my.php?image=pantallazohu0.jpg)

---

### Post by dannytatom on 2008-12-05
Sounds like a great plan to me, so I voted it up. :)

I have a question regarding the movie thumbnailer, though.  I have a rather slow laptop, that doesn't like a lot of things running at once.  Does this run constantly, looking for thumbnails everytime I open nautilus or does it look for new ones when it sees a new file and saves the thumbnail?

Sorry for the silly question. :o

---

### Post by Yuzem on 2008-12-05
> **dannytatom said:**
> Sounds like a great plan to me, so I voted it up. :)
Thanks :D

> **dannytatom said:**
> 
I have a question regarding the movie thumbnailer, though.  I have a rather slow laptop, that doesn't like a lot of things running at once.  Does this run constantly, looking for thumbnails everytime I open nautilus or does it look for new ones when it sees a new file and saves the thumbnail?
It look for new ones when it sees a new file. The thumbnail is saved. Actually, is the file manager (nautilus/thunar) that tells the thumbnailer to make a thumbnail when it sees a file without thumbnail. It work like any other thumbnailer. Nothing is running constantly in the background.

---

### Post by dannytatom on 2008-12-05
Awesome, then! & I forgot to say thanks for making this, it's wonderful. :)

---

### Post by dannytatom on 2008-12-05
Sorry to keep bumping this, but it's not working for me.  Is there something special the video file needs other than to be named correctly?

**Edit:** It seems I don't have a ~/.imdb-thumbnailer/ folder, or a config file inside of it.  I tried running 'gedit ~/.imdb-thumbnailer/config' anyway, it opened a blank text editor, but wouldn't let me save what I wrote.

Should I go ahead and create the directory and file myself, or no?

---

### Post by QwUo173Hy on 2008-12-15
I'm getting this error

> jarlath@jarlath-laptop:~$ imdb-thumbnailer 
Traceback (most recent call last):
  File "<string>", line 1, in <module>
RuntimeError: unknown error
stat: cannot stat `': No such file or directory
stat: cannot stat `': No such file or directory
couldn't parse command-line options: Cannot parse integer value '' for -s
jarlath@jarlath-laptop:~$ 


My config looks like this:
> films_path[1]=/home/jarlath/Videos

---

### Post by Yuzem on 2008-12-15
That is a bug but you must type some arguments. Try this:
```
imdb-thumbnailer --help
```

---

### Post by QwUo173Hy on 2008-12-15
Oh, ok Yuzem. I thought it would work automatically like Avatar Factory did. I'll try that :)

Thanks for your work!

---

### Post by ralphmerridew on 2009-01-18
The --unset-nautilus option doesn't remove it.

1:  It appears the test "[[ $1 = "-r" ]] && ..." is failing, so $thumbnailer isn't changed.
2:  Even if that worked, the call to gconftool ignores $thumbnailer.

---

### Post by Yuzem on 2009-01-18
What a strange thing...
Could it be a bug in bash? Are you using Intrepid? I'm using hardy and I think it is working correctly here.

Can you test this:
```
test=-r
[[ $test = "-r" ]] && echo yes
```
Does it say yes?

Maybe replacing line 221 with:
```
		[[ $1 ]] && thumbnailer='/usr/bin/gnome-video-thumbnailer -s %s %u %o'
```

Thanks for reporting. :)

---

### Post by Fabioamd87 on 2009-02-01
2 question:

this work on ArchLinux?
if yes, in what format should be the film name?

I've tried with "the truman show (1998).avi" but nothing...

---

### Post by Yuzem on 2009-02-01
It works on nautilus and thunar (gnome or xfce).
I think that it should work also in kde but I don't know how to set the thumbnailer.

It uses google to search, the first result is taken. From your example:
[URL="http://www.google.com.ar/search?hl=es&client=firefox-a&rls=com.ubuntu%3Aes-AR%3Aunofficial&hs=SCK&q=site%3Aimdb.com%2Ftitle+the+truman+show+(1998)&btnG=Buscar&meta="]
site:imdb.com/title the truman show (1998)[/URL]

In that case it should work also without the year, it is very flexible.
Maybe you haven't set the thumbnailer. Read the instructions:
```
imdb-thumbnailer --help
```

If you are using nautilus, nautilus does not update the thumbnail when the file is renamed, you have to update it manually:
```
imdb-thumbnailer -u video1.avi video2.avi etc...
```

---

### Post by Fabioamd87 on 2009-02-01
mmm this is not the right cover...

---

### Post by Yuzem on 2009-02-01
That is very strange, I just created a text file named "The Truman Show (1998).avi" and I get the right cover.

Are you using thunar or nautilus?

Try this at the command line:
(Replace /films/path and be sure that those files don't exist or they will be overwrite)
```
> "/films/path/The  Truman Show (1998) 1.avi"
```
and/or:
```
> "/films/path/The  Truman Show.avi"
```

Do they get the right cover?

---

### Post by Fabioamd87 on 2009-02-01
what kind of command is this?

---

### Post by Yuzem on 2009-02-01
It creates those files, you can use "touch" instead:

```
touch "/films/path/The  Truman Show.avi"
```

"touch" is better since it doesn't overwrite any file.

">" is used normally like this:

```
echo "testing" > ~/Desktop/test
```

It creates a file named test in your desktop containing the text: "testing"

---

### Post by Fabioamd87 on 2009-02-01
don't work... no cover...

---

### Post by Yuzem on 2009-02-01
I test it with thunar. Maybe you are using nautilus and nautilus detects that it isn't a video.

If that movie is the only one with that problem you can try this:

```
imdb-thumbnailer --set /path/to/the/movie.avi "http://ia.media-imdb.com/images/M/MV5BNjMxMjYxODk3OV5BMl5BanBnXkFtZTcwNjA1NDAzMQ@@._V1._SX99_SY140_.jpg"
```

Replace /path/to/the/movie.avi with the real path to the movie.

---

### Post by Fabioamd87 on 2009-02-02
no the problem is that the majority of the video take that strange cover :S

I'm using nautilus

---

### Post by Yuzem on 2009-02-02
Ok, can you try this:

```
bash -x imdb-thumbnailer "file://full_path_to_video.avi" ~/Desktop/test.png &> ~/Desktop/info.txt
```

Replace "full_path_to_video.avi" with some film that isn't giving the right cover, it has to end looking something like this:
```
"file:///home/your_user/Films/movie.avi"
```

Two files should be created in your desktop: test.png (the wrong cover) and info.txt

Can you post the content of info.txt or to attach the file?

---

### Post by Fabioamd87 on 2009-02-02
here the info

---

### Post by Yuzem on 2009-02-02
You need to put three slashes after "file:" like this:
```
file:///media/mulo/Incoming/The Truman Show (1998).avi
```
It seems that you used only two:
```
file://media/mulo/Incoming/The Truman Show (1998).avi
```

---

### Post by Fabioamd87 on 2009-02-02
sry, here

---

### Post by Yuzem on 2009-02-02
Ok, I think I know what the problem is.

Do this:
```
sudo gedit /usr/bin/imdb-thumbnailer
```

Line 421 should look something like this:
```
		search_term=$(echo "${SOURCE_input##*/}" | sed -e 's/[cC][dD][1-9]//' -e 's/[\(][1-9][oO][fF][1-9][\)]//' -e 's/[1-9][oO][fF][1-9]//' -e 's/[_-\.]/ /g' -e 's\....$\\' -e 's/ /+/g' -e 's/(/%28/g' -e 's/)/%29/g')
```
Replace that line with this:
```
		search_term=$(echo "${SOURCE_input##*/}" | sed -e 's/[cC][dD][1-9]//' -e 's/[\(][1-9][oO][fF][1-9][\)]//' -e 's/[1-9][oO][fF][1-9]//' -e 's/[_-.]/ /g' -e 's\....$\\' -e 's/ /+/g' -e 's/(/%28/g' -e 's/)/%29/g')
```

Now try:
```
imdb-thumbnailer -u some/film.avi
```

Does it work now?

---

### Post by Fabioamd87 on 2009-02-03
nothing...

---

### Post by Yuzem on 2009-02-03
mmm... can you try the following:

Replace line 421 with this:
```
search_term=${SOURCE_input##*/} search_term=${search_term%.*} search_term=${search_term// /+}
```

Again:
```
imdb-thumbnailer -u some/film.avi
```

That should work, I have replaced sed completely. The strange thing is that it is working perfectly on my system, thats why I can test it my self.

If for some reason that neither work, can you do this again:
```
bash -x imdb-thumbnailer "file:///media/mulo/Incoming/The Truman Show (1998).avi" ~/Desktop/test.png &> ~/Desktop/info.txt
```

---

### Post by Fabioamd87 on 2009-02-03
ok now the cover "test.png" is right but i can't see the thumbnail...
here the log

ohhh nice now it works

what was the problem?

---

### Post by Yuzem on 2009-02-03
> **Fabioamd87 said:**
> what was the problem?
There were some errors with my "sed" expressions, in my system the result was returned anyway but not in your system.

Now that I think I know what the problem was I am using sed again but I don't want to release it without being sure that it works, so... if you can test it... here it is.

I am not sure if you can install deb packages on archlinux, I also attached the source.

---

### Post by Whukes on 2009-02-07
I made a PKGBUILD for arch users and put it on the AUR.  Thanks for this Yuzem it is wonderful!

[http://aur.archlinux.org/packages.php?ID=23725](http://aur.archlinux.org/packages.php?ID=23725)

```
# Contributor: Whukes

arch=('i686' 'x86_64') #I do not have 64. Please, send me info if it does not work.
license=('GPL')
pkgname=imdb-thumbnailer
pkgver=0.7.0
pkgrel=1
pkgdesc="A video thumbnailer that sets film covers as thumbnails."
depends=('imagemagick')
url="https://launchpad.net/imdb-thumbnailer"
source=(http://launchpad.net/imdb-thumbnailer/trunk/${pkgver}/+download/imdb-thumbnailer-${pkgver}.tar.bz2)
md5sums=('5284cf224d5fc797a0d45e27f55ebe61')

build(){

#bin
mkdir -pv $startdir/pkg/usr/bin
cp -v $startdir/src/imdb-thumbnailer $startdir/pkg/usr/bin/
chmod a+x $startdir/pkg/usr/bin/imdb-thumbnailer
}

```

---

### Post by Yuzem on 2009-02-08
> **Whukes said:**
> I made a PKGBUILD for arch users and put it on the AUR.
I had tried to make a slackware package (archlinux package) using "epm" but it fails. :(

> **Whukes said:**
> Thanks for this Yuzem it is wonderful!
You are welcome!

---

### Post by DarkJesus on 2009-02-09
Tried it on arch linux. Most videos default to the default thumbnailer and the ones that it does work with get set to this:

[http://www.imdb.com/media/rm604543232/tt0045866](http://www.imdb.com/media/rm604543232/tt0045866)

I can set those video thumbnails manually though.

---

### Post by Fabioamd87 on 2009-02-09
> **DarkJesus said:**
> Tried it on arch linux. Most videos default to the default thumbnailer and the ones that it does work with get set to this:

[http://www.imdb.com/media/rm604543232/tt0045866](http://www.imdb.com/media/rm604543232/tt0045866)

I can set those video thumbnails manually though.

infact
[http://ubuntuforums.org/showpost.php?p=6657744&postcount=37](http://ubuntuforums.org/showpost.php?p=6657744&postcount=37)

but when I appliet the patch it worked

---

### Post by Yuzem on 2009-02-09
> **DarkJesus said:**
> Tried it on arch linux. Most videos default to the default thumbnailer and the ones that it does work with get set to this:

[http://www.imdb.com/media/rm604543232/tt0045866](http://www.imdb.com/media/rm604543232/tt0045866)


Did you tried the [new version]("http://www.gnomefiles.org/app.php/imdb-thumbnailer") (0.7.2)?

---

### Post by VCoolio on 2009-02-13
First of all thanks for the app, works pretty good. Only for me it doesn't affect files in folders within folders I added to the config file (and isn't that what 'recursively' means? sorry, no native English speaker). Can I do something about it? Should I add some parameter in the config file? Using Intrepid and Nautilus. Thanks.

---

### Post by Yuzem on 2009-02-13
> **VCoolio said:**
> First of all thanks for the app, works pretty good. 
You are welcome!
> **VCoolio said:**
> Only for me it doesn't affect files in folders within folders I added to the config file (and isn't that what 'recursively' means? sorry, no native English speaker). Can I do something about it? Should I add some parameter in the config file? Using Intrepid and Nautilus. Thanks.
[Hope it works now.]("http://www.gtkfiles.org/app.php/imdb-thumbnailer")

---

### Post by VCoolio on 2009-02-14
Brilliant! I didn't even have to update the thumbnails. Thanks a lot again.

---

### Post by stormtrooprdave on 2009-02-14
I have my films on a NAS drive and when I try to update them I keep getting an error message, e.g.

touch: setting times of `/media/NetworkSpace/Video/Transformers.avi': Operation not permitted

I used the command imdb-thumbnailer --update /media/NetworkSpace/Video/*.avi to try and update them all at once and it gave the same error for each file.

My config shows this:

films_path[1]=/media/NetworkSpace/Video

What is wrong?

---

### Post by stormtrooprdave on 2009-02-14
The thumbnails have changed now, still getting the error but I did

imdb-thumbnailer --remove /media/NetworkSpace/Video/*.avi

imdb-thumbnailer --update /media/NetworkSpace/Video/*.avi

It still gives the error but they did all change.

I still have one or two stand up shows that are not on imbd, I got the dvd cover off another site and downloaded it and resized it to 84x128 and tried to set it as a custom thumbnail using

imdb-thumbnailer --remove "/media/NetworkSpace/Video/frankie boyle live.avi"

imdb-thumbnailer --set "/media/NetworkSpace/Video/frankie boyle live.avi" "/media/NetworkSpace/Pictures/Misc/frankieboyle.jpg"

but it didn't work.  How can I do it?

---

### Post by binbash on 2009-02-17
> **Yuzem said:**
> You are welcome!

[Hope it works now.]("http://www.gtkfiles.org/app.php/imdb-thumbnailer")

It does not work here.I have a folder called Videos and under that folder there are over 1000 folders.I added the Videos folder to config file tried to update etc but it does not work.

---

### Post by Fabioamd87 on 2009-02-17
I Wont to disinstall this app but first remove the thumbnails, but I get this error:

```
[fabio@abuarch Incoming]$ imdb-thumbnailer --remove Amy\ McDonald\ -\ Run.avi 

(process:6276): libgnomevfs-CRITICAL **: gnome_vfs_get_uri_from_local_path: assertion `g_path_is_absolute (local_full_path)' failed
Traceback (most recent call last):
  File "<string>", line 1, in <module>
RuntimeError: unknown error
[fabio@abuarch Incoming]$
```

---

### Post by binbash on 2009-02-18
Bump..Any updates?

---

### Post by Yuzem on 2009-02-18
Sorry, I didn't get a notification.

> **stormtrooprdave said:**
> I have my films on a NAS drive and when I try to update them I keep getting an error message, e.g.

touch: setting times of `/media/NetworkSpace/Video/Transformers.avi': Operation not permitted

I used the command imdb-thumbnailer --update /media/NetworkSpace/Video/*.avi to try and update them all at once and it gave the same error for each file.

My config shows this:

films_path[1]=/media/NetworkSpace/Video

What is wrong?
It could be a problem with permissions. Try the following command if you don't mind changing the modification time (imdb-thumbnailer only change it by 1 second):
```
touch `/media/NetworkSpace/Video/Transformers.avi'
```
If that fails then it is probable a permission problem, try:
```
sudo touch `/media/NetworkSpace/Video/Transformers.avi'
```


> **stormtrooprdave said:**
> The thumbnails have changed now, still getting the error but I did

imdb-thumbnailer --remove /media/NetworkSpace/Video/*.avi

imdb-thumbnailer --update /media/NetworkSpace/Video/*.avi

It still gives the error but they did all change.

I still have one or two stand up shows that are not on imbd, I got the dvd cover off another site and downloaded it and resized it to 84x128 and tried to set it as a custom thumbnail using

imdb-thumbnailer --remove "/media/NetworkSpace/Video/frankie boyle live.avi"

imdb-thumbnailer --set "/media/NetworkSpace/Video/frankie boyle live.avi" "/media/NetworkSpace/Pictures/Misc/frankieboyle.jpg"

but it didn't work.  How can I do it?
Maybe the same problem. The cover should have been settled but the file not updated, try:
```
sudo touch "/media/NetworkSpace/Video/frankie boyle live.avi"
```
By the way: there is no need to use --remove before --set.

> **binbash said:**
> It does not work here.I have a folder called Videos and under that folder there are over 1000 folders.I added the Videos folder to config file tried to update etc but it does not work.
Ok, thats a lot of folders... :D
It shouldn't be any problems with that...
Can you try this and post the file ~/imdbt.txt
```
bash -x imdb-thumbnailer "file://full_path_to_video.avi" ~/imdbt.png &> ~/imdbt.txt
```

> **Fabioamd87 said:**
> I Wont to disinstall this app but first remove the thumbnails, but I get this error:

```
[fabio@abuarch Incoming]$ imdb-thumbnailer --remove Amy\ McDonald\ -\ Run.avi 

(process:6276): libgnomevfs-CRITICAL **: gnome_vfs_get_uri_from_local_path: assertion `g_path_is_absolute (local_full_path)' failed
Traceback (most recent call last):
  File "<string>", line 1, in <module>
RuntimeError: unknown error
[fabio@abuarch Incoming]$
```
Try the full path.

---

### Post by stormtrooprdave on 2009-02-18
Thanks worked perfectly - great app by the way

---

### Post by binbash on 2009-02-18
I emptied the Videos folder and put 10 vids with folders then gave your command.Here is the output : 

nyn@nyn-laptop:~$ cat imdbt.txt 
+ version=0.7.3
+ themes_PATH=/usr/local/share/avatar-factory/themes
+ size=128
+ video_extensions='
		/desktop/gnome/thumbnailers/application@ogg
		/desktop/gnome/thumbnailers/application@smil
		/desktop/gnome/thumbnailers/application@vnd.rn-realmedia
		/desktop/gnome/thumbnailers/application@vnd.rn-realvideo
		/desktop/gnome/thumbnailers/application@x-extension-m4a
		/desktop/gnome/thumbnailers/application@x-extension-mp4
		/desktop/gnome/thumbnailers/application@x-flash-video
		/desktop/gnome/thumbnailers/application@x-matroska
		/desktop/gnome/thumbnailers/application@x-ms-asf
		/desktop/gnome/thumbnailers/application@x-ogg
		/desktop/gnome/thumbnailers/application@x-quicktime-media-link
		/desktop/gnome/thumbnailers/application@x-shockwave-flash
		/desktop/gnome/thumbnailers/application@x-shorten
		/desktop/gnome/thumbnailers/application@x-smil
		/desktop/gnome/thumbnailers/application@xspf@xml
		/desktop/gnome/thumbnailers/audio@x-pn-realaudio
		/desktop/gnome/thumbnailers/image@vnd.rn-realpix
		/desktop/gnome/thumbnailers/image@vnd.rn-realpix
		/desktop/gnome/thumbnailers/misc@ultravox
		/desktop/gnome/thumbnailers/video@3gpp
		/desktop/gnome/thumbnailers/video@dv
		/desktop/gnome/thumbnailers/video@mp4
		/desktop/gnome/thumbnailers/video@mpeg
		/desktop/gnome/thumbnailers/video@msvideo
		/desktop/gnome/thumbnailers/video@quicktime
		/desktop/gnome/thumbnailers/video@vnd.divx
		/desktop/gnome/thumbnailers/video@vnd.rn-realvideo
		/desktop/gnome/thumbnailers/video@x-anim
		/desktop/gnome/thumbnailers/video@x-avi
		/desktop/gnome/thumbnailers/video@x-flc
		/desktop/gnome/thumbnailers/video@x-fli
		/desktop/gnome/thumbnailers/video@x-m4v
		/desktop/gnome/thumbnailers/video@x-matroska
		/desktop/gnome/thumbnailers/video@x-mpeg
		/desktop/gnome/thumbnailers/video@x-ms-asf
		/desktop/gnome/thumbnailers/video@x-msvideo
		/desktop/gnome/thumbnailers/video@x-ms-wmv
		/desktop/gnome/thumbnailers/video@x-nsv
		/desktop/gnome/thumbnailers/video@x-ogm@ogg
		'
+ [[ -z '' ]]
+ config_FILE=/home/nyn/.imdb-thumbnailer/config
+ '[' -f /home/nyn/.imdb-thumbnailer/config ']'
+ . /home/nyn/.imdb-thumbnailer/config
++ theme_name=shadow
++ films_path[1]=/home/nyn/Videos/
++ films_path[2]=
++ films_path[3]=
+ [[ -z file:///home/nyn/Videos ]]
+ parameters='file:///home/nyn/Videos /home/nyn/imdbt.png'
+ '[' file:///home/nyn/Videos '!=' '' ']'
+ case $1 in
+ [[ -z '' ]]
+ SOURCE=file:///home/nyn/Videos
+ SOURCE_input=file:///home/nyn/Videos
+ shift
+ '[' /home/nyn/imdbt.png '!=' '' ']'
+ case $1 in
+ [[ -z file:///home/nyn/Videos ]]
+ [[ -z '' ]]
+ OUTPUT_path=/home/nyn/imdbt.png
+ shift
+ '[' '' '!=' '' ']'
++ echo file:///home/nyn/Videos
++ sed 's|'\''|\\'\''|g'
+ SOURCE_input=file:///home/nyn/Videos
++ python -c 'import gnomevfs; print gnomevfs.get_local_path_from_uri('\''file:///home/nyn/Videos'\'')'
+ SOURCE_input=/home/nyn/Videos
++ stat --format=%y /home/nyn/Videos
+ file_time='2009-02-16 22:04:16.000000000 +0200'
+ file_time='2009-02-16 22:04:16'
++ stat --format=%s /home/nyn/Videos
+ file_size=4096
+ cover_name='2009-02-16 22:04:16-4096'
+ cover_path=/home/nyn/.imdb-thumbnailer/covers
+ [[ -f /home/nyn/.imdb-thumbnailer/covers/2009-02-16 22:04:16-4096.png ]]
+ [[ -z '' ]]
+ [[ -z '' ]]
+ [[ -n /home/nyn/Videos/ ]]
+ total=3
+ (( i=1 ))
+ (( i<=total ))
+ [[ /home/nyn/Videos = \/\h\o\m\e\/\n\y\n\/\V\i\d\e\o\s\/\/* ]]
+ (( i+=1 ))
+ (( i<=total ))
+ [[ /home/nyn/Videos = \/* ]]
+ folder2filter=
+ break
+ [[ -z '' ]]
+ default_video_thumbnailer
++ which gnome-video-thumbnailer
+ [[ -n /usr/bin/gnome-video-thumbnailer ]]
+ gnome-video-thumbnailer -s 128 file:///home/nyn/Videos /home/nyn/imdbt.png
** Message: Error: "/home/nyn/Videos" is a directory.
gstfilesrc.c(1038): gst_file_src_start (): /GstPlayBin:play/GstFileSrc:source

** Message: Error: "/home/nyn/Videos" is a directory.
gstfilesrc.c(1038): gst_file_src_start (): /GstPlayBin:play/GstFileSrc:source

+ exit

PS i don't want to do this for every video file i just want to show the folder and the script will find the movies under that folders (and inside the videos under that folder also) etc.I guess this can be done?

---

### Post by binbash on 2009-02-21
bump

---

### Post by Yuzem on 2009-02-21
Sorry, I didn't get a notification, again... I checked my control panel and it is configured as "instant" notification so I don't know what happens...

It seems that you are running the command on the folder instead of the video file.

If you want to update all videos in one folder (not recursively):
```
imdb-thumbnailer -u /home/nyn/Videos/*.*
```

If you want to update all the thumbnails recursively you can use the find command to do it:
```
find /home/nyn/Videos/* -type f | while read -r line ; do imdb-thumbnailer -u "$line" ; done
```

Another way is to delete the folder where the thumbnails are but it will delete all thumbnails (for pictures,pdfs,all videos, etc):
```
 rm -r ~/.thumbnails/normal/
```

---

### Post by binbash on 2009-02-21
Thanks for reply, here is what i did : 

First i removed the thumbnails , then

I both tried recursively and folder commands, but i still get nautilus thumbnails instead of covers etc.

---

### Post by Yuzem on 2009-02-21
Maybe it isn't configured correctly...
Try this:
```
imdb-thumbnailer --set-nautilus
```

And:
```
echo 'films_path[1]=/home/nyn/Videos' > /home/nyn/.imdb-thumbnailer/config
```

Just in case:
```
killall nautilus
```

Does it work now?

---

### Post by binbash on 2009-02-21
I re-set nautilus (i set it before), and add it to the config via your command and killed nautilus.Then it works.Thanks for your help BUT i did your steps before (especially config and set nautilus), it didn't work but this time it is done.

Again thanks for your help Yuzem

---

### Post by Dawei87 on 2009-02-28
just found this online and thought i would give it a try. i installed it fine and put the path to my videos in the config, but im still not getting any covers, just basic thumbnails. i never got any errors, and i can run the update command fine and everything and even did a restart but still no luck. any suggestions?

---

### Post by Yuzem on 2009-03-02
Sorry for the delay, I am getting delayed notifications... :(

Did you tried:
```
imdb-thumbnailer --set-nautilus
```
or
```
imdb-thumbnailer --set-thunar
```

---

### Post by Dawei87 on 2009-03-02
yea, i did that and it scrolled down setting all the video formats to be used. it seemed to run through ok, and i set my path to the videos in the config, but nothing happens when i update. if i type a command in the terminal for one specific film to update, then the thumbnail i have by default disappears for a few seconds, and then there is a regular icon, but then the default thumbnail returns again.

---

### Post by Yuzem on 2009-03-02
> **Dawei87 said:**
> if i type a command in the terminal for one specific film to update, then the thumbnail i have by default disappears for a few seconds, and then there is a regular icon, but then the default thumbnail returns again.

Can you run that command but with bash -x before and post the result?:
```
bash -x imdb-thumbnailer -u some-film.avi
```

---

### Post by Dawei87 on 2009-03-02
i will try that comman asap. i am at work at the moment though so it will take me a minute

---

### Post by Dawei87 on 2009-03-03
david@master:~$ bash -x imdb-thumbnailer -u ~/Videos/Video/Primer.avi
+ version=0.7.3
+ themes_PATH=/usr/local/share/avatar-factory/themes
+ size=128
+ video_extensions='
		/desktop/gnome/thumbnailers/application@ogg
		/desktop/gnome/thumbnailers/application@smil
		/desktop/gnome/thumbnailers/application@vnd.rn-realmedia
		/desktop/gnome/thumbnailers/application@vnd.rn-realvideo
		/desktop/gnome/thumbnailers/application@x-extension-m4a
		/desktop/gnome/thumbnailers/application@x-extension-mp4
		/desktop/gnome/thumbnailers/application@x-flash-video
		/desktop/gnome/thumbnailers/application@x-matroska
		/desktop/gnome/thumbnailers/application@x-ms-asf
		/desktop/gnome/thumbnailers/application@x-ogg
		/desktop/gnome/thumbnailers/application@x-quicktime-media-link
		/desktop/gnome/thumbnailers/application@x-shockwave-flash
		/desktop/gnome/thumbnailers/application@x-shorten
		/desktop/gnome/thumbnailers/application@x-smil
		/desktop/gnome/thumbnailers/application@xspf@xml
		/desktop/gnome/thumbnailers/audio@x-pn-realaudio
		/desktop/gnome/thumbnailers/image@vnd.rn-realpix
		/desktop/gnome/thumbnailers/image@vnd.rn-realpix
		/desktop/gnome/thumbnailers/misc@ultravox
		/desktop/gnome/thumbnailers/video@3gpp
		/desktop/gnome/thumbnailers/video@dv
		/desktop/gnome/thumbnailers/video@mp4
		/desktop/gnome/thumbnailers/video@mpeg
		/desktop/gnome/thumbnailers/video@msvideo
		/desktop/gnome/thumbnailers/video@quicktime
		/desktop/gnome/thumbnailers/video@vnd.divx
		/desktop/gnome/thumbnailers/video@vnd.rn-realvideo
		/desktop/gnome/thumbnailers/video@x-anim
		/desktop/gnome/thumbnailers/video@x-avi
		/desktop/gnome/thumbnailers/video@x-flc
		/desktop/gnome/thumbnailers/video@x-fli
		/desktop/gnome/thumbnailers/video@x-m4v
		/desktop/gnome/thumbnailers/video@x-matroska
		/desktop/gnome/thumbnailers/video@x-mpeg
		/desktop/gnome/thumbnailers/video@x-ms-asf
		/desktop/gnome/thumbnailers/video@x-msvideo
		/desktop/gnome/thumbnailers/video@x-ms-wmv
		/desktop/gnome/thumbnailers/video@x-nsv
		/desktop/gnome/thumbnailers/video@x-ogm@ogg
		'
+ [[ -z '' ]]
+ config_FILE=/home/david/.imdb-thumbnailer/config
+ '[' -f /home/david/.imdb-thumbnailer/config ']'
+ . /home/david/.imdb-thumbnailer/config
++ films_path[1]=/home/David/Videos/Video/
+ [[ -z -u ]]
+ parameters='-u /home/david/Videos/Video/Primer.avi'
+ '[' -u '!=' '' ']'
+ case $1 in
+ shift
+ '[' /home/david/Videos/Video/Primer.avi '!=' '' ']'
+ update_thumbnail /home/david/Videos/Video/Primer.avi
+ file_path=/home/david/Videos/Video/Primer.avi
+ [[ -f /home/david/Videos/Video/Primer.avi ]]
++ stat --format=%y /home/david/Videos/Video/Primer.avi
+ file_time='2009-02-10 11:48:49.000000000 -0800'
+ file_time='2009-02-10 11:48:49'
++ stat --format=%s /home/david/Videos/Video/Primer.avi
+ file_size=734001152
+ cover_name='2009-02-10 11:48:49-734001152'
+ cover_path=/home/david/.imdb-thumbnailer/covers
+ second=9
+ case $second in
+ second=8
+ incomplete_time='2009-02-10 11:48:4'
+ new_cover_name='2009-02-10 11:48:48-734001152'
+ [[ -f /home/david/.imdb-thumbnailer/covers/2009-02-10 11:48:49-734001152.png ]]
+ touch /home/david/Videos/Video/Primer.avi -d '2009-02-10 11:48:48'
+ shift
+ '[' '' '!=' '' ']'
+ exit
david@master:~$

ok. i did that and it looks like evrything should be ok, but it still doesnt replace the thumbnail i already have with anything

---

### Post by Yuzem on 2009-03-04
It could be maybe that in your config you have:
```
films_path[1]=/home/David/Videos/Video/
```
While it should be:
```
films_path[1]=/home/David/Videos/Video
```
Without the last /

---

### Post by Dawei87 on 2009-03-04
ok. i tried that, im getting the same results. thanks for trying to help me with this, i have tons of movies and this looks so cool!

---

### Post by Yuzem on 2009-03-04
Can you try this?:
```
bash -x imdb-thumbnailer "file:///home/david/Videos/Video/Primer.avi" ~/imdbt.png &> ~/imdbt.txt
```

And attach ~/imdbt.txt or post its content.
That should reveal whats going on...

---

### Post by Dawei87 on 2009-03-04
ok. here ya go. it also put a copy of the thumbnail i already have in my home folder, which was odd. it never did that before.

---

### Post by Yuzem on 2009-03-04
> **Dawei87 said:**
> It also put a copy of the thumbnail i already have in my home folder, which was odd.
Yes, that is just for the test...
I think that the problem is that you have David instead of david in the config. It should be:
```
films_path[1]=/home/david/Videos/Video
```

Hope it works now. ;)

---

### Post by Dawei87 on 2009-03-05
wow. worked like a charm. (i feel like an idiot now). thank you so much for helping and being patient with me! and good job, i love the thumbnails!

---

### Post by VCoolio on 2009-04-24
Hi, thanks again for this app, used it for the last months. I updated to Jaunty and it doesn't seem to work anymore. Could you please look into it?

---

### Post by Yuzem on 2009-04-24
Are you using thunar or nautilus?
Did you tried:
```
imdb-thumbnailer --set-nautilus
```
or
```
imdb-thumbnailer --set-thunar
```

---

### Post by VCoolio on 2009-04-24
Thanks for the reply. Yeah, I did the nautilus one, it ran like it should. (several lines of output like "Seting Key for ..."; should be setting btw, not seting). And I use the config that worked in Intrepid and the paths are correct. Are there dependecies I need? (I did a clean new install). I do have imagemagick already, couldn't live without it.

---

### Post by Yuzem on 2009-04-24
> **VCoolio said:**
> (should be setting btw, not seting)
Fixed, thanks.
> **VCoolio said:**
> Are there dependecies I need?
No, only imagemagick.

I will check in Jaunty when I get it completely installed. Meanwhile you could try:

```
sudo gedit $(which imdb-thumbnailer)
```

After the first line insert:
```
zenity --info
```

Now try updating a thumbnail inside the configured path:
```
imdb-thumbnailer -u "video.avi"
```

If a dialog appears then the thumbnailer is correctly settled.

---

### Post by VCoolio on 2009-04-25
Sorry, the problem is something else. On my /home section the thumbnailer still works, but on my other partition it doesn't. After clean install I had nothing in /home to test it on, but I just thought of this. Don't know what the problem is yet, probably something with automount or permissions, will post here if I find out. Sorry again for bothering you too early.
EDIT: no luck yet. Changed to automount. About the permissions I'm not sure. I did a chown -R for my username but nautilus tells me root still owns that partition (sigh). I can read/write though, only the thumbnailer doesn't work, afaik. Ideas are welcome.

---

### Post by Yuzem on 2009-04-25
Are other thumbnailers working? (Sorry for my english)
For example, what about pictures? Do they get thumbnails?

You could also check in nautilus > edit > preferences > and I don't know how it is in english, previous view or something like that (one tab before the last one in Hardy). There is an option for thumbnails that you can change from "Only on local files" to Always.

---

### Post by VCoolio on 2009-04-25
Thanks for not giving up. Pictures have thumbnails, and videos have a thumbnail with a frame / shot from the movie. When I try to update the thumbnail with imdb-thumbnailer, the icon changes to a sort of "changing/thinking" icon, but then uses the old preview again. The terminal gives no output / error on this.

---

### Post by Yuzem on 2009-04-25
It seems that the problem is on imdb-thumbnailer.
Then, the problem is that imdb-thumbnailer doesn't work on some paths (your other partition)?

Could you post your config?
```
cat ~/.imdb-thumbnailer/config
```

[Do you did this?]("http://ubuntuforums.org/showpost.php?p=7138780&postcount=89")
Did a dialog appeared?

---

### Post by VCoolio on 2009-04-25
This is so stupid. I already noticed that the mount point for my windows partition had changed compared to intrepid. So, I changed that in the config file too. I thought. Appears I didn't, or didn't save it, or whatever. ](*,)
Anyway, trying to copypaste my config here I saw the problem. It works again. Sorry for the confusion. Stay happy.

---

### Post by Rizlaw on 2009-05-03
After reading all 94 posts on this thread, I downloaded and successfully installed version 0.7.3 of Yuzem's very nice script into one of my Ubuntu 9.04 systems for a test. In the config file I set:

                    films_path[1]=/home/username/Videos.

In the "Videos" folder I had two movies: THE DAY THE EARTH STOOD STILL.mkv and FORBIDDEN PLANET.mkv". Note that there are "spaces" in the file names, I normally don't use "_" between words in filenames.

Both files had icons from a random frame of each movie.

I opened a terminal in the Video folder and ran:

 imdb-thumbnailer --update THE DAY THE EARTH STOOD STILL.mkv FORBIDDEN PLANET.mkv 

I saw no change in the icons - no movie covers. I then looked back at the early postings and noticed a part of a reply where Yuzem stated that file names with "spaces" in the file name might not be correctly found when global search terms are used. However, I hadn't used any global search terms, i.e. "*.*".

Nevertheless, I went back and renamed both file names to include "_" in the file names: THE_DAY_THE_EARTH_STOOD_STILL.mkv and FORBIDDEN_PLANET.mkv.

I ran the the command again with the new file names:

 imdb-thumbnailer --update THE_DAY_THE_EARTH_STOOD_STILL.mkv FORBIDDEN_PLANET.mkv

It worked! 

So here's my question with respect to using the following command (non-recursively):

   imdb-thumbnailer -u /home/username/Videos/*.*

If a person has a film library with file names that have "spaces" in the file names must all of those file names be converted into file names with "_" in the names before this program will successfully retrieve movie covers?

---

### Post by fooman on 2009-05-03
> **Rizlaw said:**
> 
If a person has a film library with file names that have "spaces" in the file names must all of those file names be converted into file names with "_" in the names before this program will successfully retrieve movie covers?

no,  that should not be necessary...i have spaces in my .avi titles and the command:

```
    imdb-thumbnailer -u /home/username/Videos/*.*
```worked fine for me.  although after doing a fresh install of jaunty and carrying over my old /home directory,  i could not get some of the thumbnails to laod after running that command.  so i first ran the *-remove* command:

```
    imdb-thumbnailer -r /home/username/Videos/*.*
```then followed that up with the *-update* command:

```
    imdb-thumbnailer -u /home/username/Videos/*.*
```and it worked like a charm.  :)

---

### Post by Rizlaw on 2009-05-03
Thanks for the reply Fooman.

---

### Post by Yuzem on 2009-05-03
> **Rizlaw said:**
> If a person has a film library with file names that have "spaces" in the file names must all of those file names be converted into file names with "_" in the names before this program will successfully retrieve movie covers?
No, all my films have spaces in their names. I name them with this format: "year - title"
I did a test, I have two movies from 1960:
```
imdb-thumbnailer -u Films/1960*.*
```
It worked, I am using hardy. The names should be expanded automatically.

Can you try the following?:
```
sudo gedit $(which imdb-thumbnailer)
```

After the first line insert:
```
set +f
```

Save it and try again.

Edit:
Ok, I read Fooman's post, I hope it works.

---

### Post by VCoolio on 2009-05-03
I noticed you updating thumbnails in terminal, which is fine of course, but maybe you would like to use nautilus. You can make a very easy nautilusscript. Copy-paste this in a texteditor:
```
#!/bin/sh
for arg 
do

 imdb-thumbnailer --update "$arg" &
 
done
```


Save somewhere. Then (in a terminal) run (each line separately):
```
sudo chmod +x /path/to/script
mv /path/to/script ~/.gnome2/nautilus-scripts

```
Now in nautilus you can do right mouse button on the file and choose scripts > whatever you named the script and the icon will be updated. Since you develop the need to update the thumbnail when you see it in Nautilus this seemed like a good opportunity for a nautilus-script. It works on multiple files at once if you select them.

---

### Post by garethfnb on 2009-05-04
New to the Linux game and very interested in Imdb-thumbnailer, just wanted to know have to get this to work through the proxy at work, any ideas?... tx

---

### Post by Yuzem on 2009-05-04
I don't know much about proxies. imdb-thumbnailer uses wget, I did a search in google and I found [this]("http://blog.taragana.com/index.php/archive/how-to-use-wget-through-proxy/")

I theory you have to do the following:
```
sudo gedit $(which imdb-thumbnailer)
```

After the first line add:
```
export http_proxy="http://username:password@proxy.example.com:8080"
```
You have to reemplace username password port etc with your settings.

Then do a search for wget, there should be 3 matches.
For every match you have to add "-proxy=on" after wget.
For example this:
```
wget -U firefox -qO - "http://www.google.com... etc
```
Must be changed to this:
```
wget -proxy=on -U firefox -qO - "http://www.google.ccom... etc
```

---

### Post by Voorhees1979 on 2009-07-13
Is there anything like this for kde's konqueror

---

### Post by RD1 on 2009-07-17
Help!!!! cli update suddenly stopped working! 

```
rodger@Bodhisattva:~/Videos$ bash -x imdb-thumbnailer --set "Forever Knight 320 - Francesa.avi" thumbnail.jpg
+ version=0.7.4
+ themes_PATH=/usr/local/share/avatar-factory/themes
+ size=128
+ covers=/home/azd/Network/Programming/figuritas/config/web/movies/movies/256
+ movie_manager='/home/azd/Network/Programming/figuritas/figuritas movies'
+ video_extensions='
		application@ogg
		application@smil
		application@vnd.rn-realmedia
		application@vnd.rn-realvideo
		application@x-extension-m4a
		application@x-extension-mp4
		application@x-flash-video
		application@x-matroska
		application@x-ms-asf
		application@x-ogg
		application@x-quicktime-media-link
		application@x-shockwave-flash
		application@x-shorten
		application@x-smil
		application@xspf@xml
		audio@x-pn-realaudio
		image@vnd.rn-realpix
		image@vnd.rn-realpix
		misc@ultravox
		video@3gpp
		video@dv
		video@mp4
		video@mpeg
		video@msvideo
		video@quicktime
		video@vnd.divx
		video@vnd.rn-realvideo
		video@x-anim
		video@x-avi
		video@x-flc
		video@x-fli
		video@x-m4v
		video@x-matroska
		video@x-mpeg
		video@x-ms-asf
		video@x-msvideo
		video@x-ms-wmv
		video@x-nsv
		video@x-ogm@ogg
	'
+ [[ -z '' ]]
+ config_FILE=/home/rodger/.imdb-thumbnailer/config
+ '[' -f /home/rodger/.imdb-thumbnailer/config ']'
+ . /home/rodger/.imdb-thumbnailer/config
++ films_path[1]=/home/rodger/Videos
++ films_path[2]=/media/500GB/Movies
++ theme_name=shadow
+ [[ -z --set ]]
+ parameters='--set Forever Knight 320 - Francesa.avi thumbnail.jpg'
+ '[' --set '!=' '' ']'
+ case $1 in
+ shift
+ '[' 'Forever Knight 320 - Francesa.avi' '!=' '' ']'
+ set_thumbnail 'Forever Knight 320 - Francesa.avi' thumbnail.jpg
+ file_path='Forever Knight 320 - Francesa.avi'
+ grabber_picture=thumbnail.jpg
+ [[ -f Forever Knight 320 - Francesa.avi ]]
+ [[ -n thumbnail.jpg ]]
++ stat --format=%y-%s 'Forever Knight 320 - Francesa.avi'
+ file_time_size='2009-07-17 12:58:16.000000000 -0400-1049186922'
+ file_time_size='2009-07-17 12:58:16-1049186922'
+ cover_name='2009-07-17 12:58:16-1049186922'
+ cover_path=/home/rodger/.imdb-thumbnailer/covers
+ [[ -d /home/rodger/.imdb-thumbnailer/covers ]]
+ convert thumbnail.jpg -thumbnail 256x256 '/home/rodger/.imdb-thumbnailer/covers/2009-07-17 12:58:16-1049186922.png'
+ update_thumbnail 'Forever Knight 320 - Francesa.avi'
+ file_path='Forever Knight 320 - Francesa.avi'
+ [[ -f Forever Knight 320 - Francesa.avi ]]
++ stat --format=%y-%s 'Forever Knight 320 - Francesa.avi'
+ file_time_size='2009-07-17 12:58:16.000000000 -0400-1049186922'
+ file_time_size='2009-07-17 12:58:16-1049186922'
+ file_time='2009-07-17 12:58:16'
+ [[ -n 2009-07-17 12:58:16 ]]
+ cover_name='2009-07-17 12:58:16-1049186922'
+ cover_path=/home/rodger/.imdb-thumbnailer/covers
+ second=6
+ case $second in
+ second=7
+ incomplete_time='2009-07-17 12:58:1'
+ new_cover_name='2009-07-17 12:58:17-'
+ [[ -f /home/rodger/.imdb-thumbnailer/covers/2009-07-17 12:58:16-1049186922.png ]]
+ mv '/home/rodger/.imdb-thumbnailer/covers/2009-07-17 12:58:16-1049186922.png' '/home/rodger/.imdb-thumbnailer/covers/2009-07-17 12:58:17-.png'
+ touch 'Forever Knight 320 - Francesa.avi' -d '2009-07-17 12:58:17'
+ shift
+ shift
+ '[' '' '!=' '' ']'
+ exit
rodger@Bodhisattva:~/Videos$ 

```

Icon changes to "working" then goes back to default thumbnail.

---

### Post by Yuzem on 2010-05-07
[There is a new version.]("http://www.gnomefiles.org/app.php/imdb-thumbnailer")

Sorry RD1, I just read your post, let me know if the problem persist.

---

### Post by draki on 2011-10-21
Does anyone have imdb-thumbnailer working in 11.10? I had it working fine in 11.04 and decided to do a clean install. But nothing I do seems to get it to work - I only have the stock gnome thumbnails

any advice would be much appreciated

thank you

---

### Post by Yuzem on 2011-10-25
> **draki said:**
> I only have the stock gnome thumbnails

So you have the standard video frame thumbnails, I think the problem is the new nautilus using dconf instead of gconf. I will take a look.

---

### Post by Yuzem on 2011-10-27
I think this should work:
```
sudo gedit /usr/share/thumbnailers/imdb.thumbnailer
```

Paste this text and save the file:
```
[Thumbnailer Entry]
TryExec=/usr/bin/imdb-thumbnailer
Exec=/usr/bin/imdb-thumbnailer -s %s %u %o
MimeType=application/mxf;application/ogg;application/ram;application/sdp;application/vnd.ms-wpl;application/vnd.rn-realmedia;application/x-extension-m4a;application/x-extension-mp4;application/x-flash-video;application/x-matroska;application/x-netshow-channel;application/x-ogg;application/x-quicktimeplayer;application/x-shorten;image/vnd.rn-realpix;image/x-pict;misc/ultravox;text/x-google-video-pointer;video/3gpp;video/dv;video/fli;video/flv;video/mp2t;video/mp4;video/mp4v-es;video/mpeg;video/msvideo;video/ogg;video/quicktime;video/vivo;video/vnd.divx;video/vnd.rn-realvideo;video/vnd.vivo;video/webm;video/x-anim;video/x-avi;video/x-flc;video/x-fli;video/x-flic;video/x-flv;video/x-m4v;video/x-matroska;video/x-mpeg;video/x-ms-asf;video/x-ms-asx;video/x-msvideo;video/x-ms-wm;video/x-ms-wmv;video/x-ms-wmx;video/x-ms-wvx;video/x-nsv;video/x-ogm+ogg;video/x-theora+ogg;video/x-totem-stream;audio/x-pn-realaudio;audio/3gpp;audio/ac3;audio/AMR;audio/AMR-WB;audio/basic;audio/midi;audio/mp2;audio/mp4;audio/mpeg;audio/ogg;audio/prs.sid;audio/vnd.rn-realaudio;audio/x-aiff;audio/x-ape;audio/x-flac;audio/x-gsm;audio/x-it;audio/x-m4a;audio/x-matroska;audio/x-mod;audio/x-mp3;audio/x-mpeg;audio/x-ms-asf;audio/x-ms-asx;audio/x-ms-wax;audio/x-ms-wma;audio/x-musepack;audio/x-pn-aiff;audio/x-pn-au;audio/x-pn-wav;audio/x-pn-windows-acm;audio/x-realaudio;audio/x-real-audio;audio/x-sbc;audio/x-speex;audio/x-tta;audio/x-wav;audio/x-wavpack;audio/x-vorbis;audio/x-vorbis+ogg;audio/x-xm;application/x-flac;

```

Now do:
```
mv /usr/share/thumbnailers/totem.thumbnailer /usr/share/thumbnailers/totem.thumbnailer.back
nautilus -q
```

Please let me know if it works.

---

### Post by draki on 2011-10-27
That seems to have fixed it Yuzem - thank you very much indeed

I needed to remove all movies and re-add them using -r and -u and all seems to be good now - my Films' folder looks great again

thank you

---

### Post by draki on 2011-10-27
> **draki said:**
> That seems to have fixed it Yuzem - thank you very much indeed

I needed to remove all movies and re-add them using -r and -u and all seems to be good now - my Films' folder looks great again

thank you

I spoke too soon

A few thumbs updated with covers so I left it thinking that they will all update

I came back a while later, applied an update and the thumbs had reverted to the Totem thumbs

I checked the changes you suggested and they are still present

It seems the folder ~/.thumbnails/fail/gnome-thumbnail-factory is full

The ~/.gconf/desktop/gnome/thumbnailers entries are still there - should I remove them?

Any further ideas?

---

### Post by Yuzem on 2011-10-27
> The ~/.gconf/desktop/gnome/thumbnailers entries are still there - should I remove them?
I believe there is no need to remove them.

Try this:
```
rm -r ~/.thumbnails/fail
imdb-thumbnailer -r some-video.avi
imdb-thumbnailer -u some-video.avi
```

If that doesn't work you can check if the thumbnailer is being used:
```
gedit .imdb-thumbnailer/config
```
And add this somewhere:
```
zenity --info
```

Then do an -r and -u on some video and see if a dialog pops before the thumbnail is made, if it does, then the thumbnailer is working, maybe you don't have the path added in the config file for that folder.

---

### Post by draki on 2011-10-27
The dialog pops up before the thumbnail is being made, but I'm sure the path is correct - this is the contents of my config file

films_path[1]=/mnt/Media/Films
films_path[2]=/home/max/Desktop
films_path[3]=

I added a film to the Desktop and tried -r -u on that, but still no joy

---

### Post by Yuzem on 2011-10-27
Make sure any of your paths is a symbolic link.
Try this:
```
touch "/home/max/Desktop/1999.Matrix.avi"
```

---

### Post by draki on 2011-10-28
That works immediately. And I'm sure there aren't any symlinks

This morning some of the thumbs have updated correctly

I think I'll leave it and see if the rest update

strange

---

### Post by Yuzem on 2011-11-08
New version [here]("http://gnomefiles.org/content/show.php?content=132112").

---

### Post by hopelessone on 2012-09-28
Hi,

Nothing is happening.

I have:
gedit ~/.imdb-thumbnailer/config
```
films_path[0]=/mnt/hdd_2/Movies
```

```
blade@pangolin:/mnt/hdd_2/Movies$ gedit ~/.imdb-thumbnailer/config
blade@pangolin:/mnt/hdd_2/Movies$ imdb-thumbnailer --update 10000\ BC\ \[2008\].mp4 
blade@pangolin:/mnt/hdd_2/Movies$ 

```

no error but Nautilus looks the same. Deleted all thumbnails. What should I check?

thanks,

---

### Post by Yuzem on 2012-09-28
Hi,
Try this:
```
imdb-thumbnailer --set-nautilus
```
Then restart nautilus:
```
nautilus -q
```
And finally the --update command again.

---

### Post by indip on 2012-10-01
It doesn't work for [me]("http://moviesonline44.blogspot.com"). Bad Luck

---

### Post by Yuzem on 2012-10-01
> **indip said:**
> It doesn't work for [me]("http://moviesonline44.blogspot.com"). Bad Luck

Have you tried:
```
imdb-thumbnailer --set-nautilus
```

...and updating the thumbnails:
```
imdb-thumbnailer -u /path/2/videos/*.*
```

---

### Post by hopelessone on 2013-09-19
Hey this is really good, got it going with the latest one..

made a quick donation of $5..

Thanks again..

---

### Post by hopelessone on 2013-09-19
Anyway to get a higher quality thumbnail? looks a bit blurred when enlarged on a 47" TV.

Thanks,

---

### Post by Yuzem on 2013-09-19
Hi hopelessone, thank you very much for the donation!

Regarding the quality, try adding the following text to the config file (~/.imdb-thumbnailer/config):
```
size=256
```

---


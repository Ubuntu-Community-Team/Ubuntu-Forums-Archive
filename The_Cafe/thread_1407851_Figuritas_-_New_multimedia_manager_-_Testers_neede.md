---
title: "Figuritas - New multimedia manager - Testers needed"
date: 2010-02-15
forum: The Cafe
---

### Post by Yuzem on 2010-02-15
Figuritas is an open source multimedia manager for linux.

Description with screenshots:
[[IMG]http://3.bp.blogspot.com/_EbNPUgfUDXs/S35zizifkbI/AAAAAAAAAsI/imKgYBOPBIk/s320/figuritas-0.jpg[/IMG]]("http://yuzem.blogspot.com/p/figuritas.html")

I am opening this thread so anyone can report any problem here.
Comments, advices and requests are welcome.

---

### Post by DeadSuperHero on 2010-02-15
Looks spiffy, although oddly close to iTunes.

---

### Post by koleoptero on 2010-02-15
The idea looks great. Nice job. :)

---

### Post by lovinglinux on 2010-02-15
Looks interesting. Good job.

---

### Post by joey-elijah on 2010-02-15
I get the wonderful

"http://localhost:9009
Error: unrecognized override.ini path." 

error on Lucid.

---

### Post by Warpnow on 2010-02-15
Conflicts with the package apache2 for some reason.

Edit: and once installed I get the same error as joey-elijah

---

### Post by zekopeko on 2010-02-15
> **joey-elijah said:**
> I get the wonderful

"http://localhost:9009
Error: unrecognized override.ini path." 

error on Lucid.

Same here. On Karmic btw.

---

### Post by Yuzem on 2010-02-16
Thanks all for the comments :)

> **Mr. Psychopath said:**
> Looks spiffy, although oddly close to iTunes.
I know, it is only a skin, it will be possible to change it in future versions.

> **joey-elijah said:**
> I get the wonderful

"http://localhost:9009
Error: unrecognized override.ini path." 

error on Lucid.
Thats a bug, type on the terminal:
```
prism
```
in URL put localhost:9009
in Name: Figuritas
and check desktop
Click Ok and try to run figuritas.
You can delete the desktop shortcut after this.

> **Warpnow said:**
> Conflicts with the package apache2
Yes, some problems were reported whith apache caused by thttpd.

---

### Post by nilarimogard on 2010-02-16
> **joey-elijah said:**
> I get the wonderful

"http://localhost:9009
Error: unrecognized override.ini path." 

error on Lucid.

After installing Figuritas, don't run it! Instead, go to *Applications > Internet > Prism*,  enter "figuritas" under the "name" and under "url", enter this:

[http://127.0.0.1:9009](http://127.0.0.1:9009)

and  that's it. Now you can run Figuritas from the menu (*Applications > Sound & Video >  Figuritas*).

Edit: didn't see the last post.

---

### Post by micmic on 2010-02-16
> **Yuzem said:**
> Thanks all for the comments :)


I know, it is only a skin, it will be possible to change it in future versions.


Thats a bug, type on the terminal:
```
prism
```
in URL put localhost:9009
in Name: Figuritas
and check desktop
Click Ok and try to run figuritas.
You can delete the desktop shortcut after this.


Yes, some problems were reported whith apache caused by thttpd.

I have the same problem with Karmic so I do this and:
```
Not allowed ip: 127.0.0.1
```
On a blank window :(

But it works with
```
http://127.0.0.1:9009/
```
:O

So I am happy :)

---

### Post by Yuzem on 2010-02-23
There is a [new version]("http://yuzem.blogspot.com").

---

### Post by Ric_NYC on 2010-02-23
Figuritas don't work-ita on my computer-ita.

---

### Post by Islington on 2010-02-23
This looks very nice; also like the idea of doing this in prism. 

I dont quite understand what it is for? is it a collection manager?

---

### Post by Warpnow on 2010-02-24
> **Islington said:**
> This looks very nice; also like the idea of doing this in prism. 

I dont quite understand what it is for? is it a collection manager?

I, too, wonder this.

---

### Post by juancarlospaco on 2010-02-24
It says is coded on Bash and HTML, interesting...

---

### Post by Yuzem on 2010-02-24
> **Ric_NYC said:**
> Figuritas don't work-ita on my computer-ita.
Could you give me more information on what isn't working?
Or try this at the terminal:
```
figuritas movies -a http://www.imdb.com/title/tt0133093/
figuritas -S &
firefox 127.0.0.1:9009
```

> **Islington said:**
> This looks very nice; also like the idea of doing this in prism. 

I dont quite understand what it is for? is it a collection manager?

Yes it can be used as a collection manager but it is intended to be a multimedia manager (not very multi right now) since you can associate your media.

For example if you have movies on your computer you can add and associate them with:
```
figuritas movies -a /path2movies/*.avi
```
There is no gui option to do that right now.

---

### Post by ctrlmd on 2010-02-24
looks great looking forward to use it 
good job :)

---

### Post by Islington on 2010-02-24
> **Yuzem said:**
> 

Yes it can be used as a collection manager but it is intended to be a multimedia manager (not very multi right now) since you can associate your media.

For example if you have movies on your computer you can add and associate them with:
```
figuritas movies -a /path2movies/*.avi
```
There is no gui option to do that right now.
Most excellent; I know the project is very new, but is there anyway that the metadata that it gathers can be written into the file? perhaps using nepomuk?

---

### Post by Yuzem on 2010-02-24
> **Islington said:**
> Most excellent
You can also use [imdb-thumbnailer]("http://yuzem.blogspot.com/p/imdb-thumbnailer.html") to automatically add and/or bind your movies with figuritas.

> **Islington said:**
> I know the project is very new, but is there anyway that the metadata that it gathers can be written into the file? perhaps using nepomuk?

This is something that I wanted to do but I never found a good way to write meta data to avi files in bash. I took a look to nepomuk but it doesn't seem to be accessible from the command line. :(

I have added a [poll]("http://yuzem.blogspot.com/2010/02/poll-what-module-do-you-want-most.html") to vote for the most wanted module. :popcorn:

---

### Post by Nonno Bassotto on 2010-02-24
I played a bit with the new version, and it seems I cannot see the movies I add. I can add them either from the command line or from the web interface, but I don't find where they should show up (I'm sure it was immediate in the previous versions; so immediate that now I'm not sure where I should look).

---

### Post by Yuzem on 2010-02-24
It is working here.
I think that you have two databases.

If you run figuritas with apache your config will be located one folder above the web folder that should be: /var/www

This is because the server doesn't give me the usual environment variables like $HOME so the index.cgi file only gets the current directory and sets the config dir one dir above.

When using thttpd as the server the web path is located on ~/.figuritas/web and the config dir is the same as the default when running figuritas from the command line: ~/.figuritas

Thats why you probable have two databases: ~/.figuritas/movies.db (when running from the cli) and /var/www/movies.db when running from the web interface.

I haven't found a solution to that problem, if you have any suggestion just let me know.

For now you could do this:
sudo gedit /usr/bin/figuritas

and change line 14 from:
```
path_config=$HOME/.figuritas
```
to:
```
path_config=/var/www
```

But I don't know if it will have permissions to edit the database.

---

### Post by micmic on 2010-02-24
> **Yuzem said:**
> ```
figuritas movies -a /path2movies/*.avi
```
There is no gui option to do that right now.

I try with this option, but it looks to work ugly with avi with spaces in their name

---

### Post by Nonno Bassotto on 2010-02-24
> **Yuzem said:**
> 
If you run figuritas with apache your config will be located one folder above the web folder that should be: /var/www


Uhm... this is a problem, since Apache does not have the rights to write directly in /var/www. If you created the database directly inside the figuritas folder (why not?) I could chmod that folder to www_data. I'd rather not do it with the whole /var/www directory, since that belongs to my user.

---

### Post by Yuzem on 2010-02-25
> **micmic said:**
> I try with this option, but it looks to work ugly with avi with spaces in their name
Are you sure? It seems to work ok for me.
What is exactly the problem?
Could you tell me you bash version?
```
bash --version
```

> **Nonno Bassotto said:**
> Uhm... this is a problem, since Apache does not have the rights to write directly in /var/www. If you created the database directly inside the figuritas folder (why not?) I could chmod that folder to www_data. I'd rather not do it with the whole /var/www directory, since that belongs to my user.
Yes, I will probably change the location of the config files. I didn't do it that way because I didn't want to make those files available from the server and I really don't know what is the standard for web apps.

There is also another approach. I could make the cli thing to be like a client. Meaning that it could access the database and other things through the server.

---

### Post by steev182 on 2010-02-25
This looks really interesting.

Can it manage TV Shows too? I really want a Media management app that lets me have a playcount of my Movies and TV shows so I can sync unwatched/favourite shows to my N900.

---

### Post by Yuzem on 2010-02-25
> **steev182 said:**
> This looks really interesting.
Can it manage TV Shows too? I really want a Media management app that lets me have a playcount of my Movies and TV shows so I can sync unwatched/favourite shows to my N900.
Yes the module "movies" can handle tv shows, actually, when viewing a tv show details there is a tab called episodes among the sub tabs but it is not implemented yet.

---

### Post by Nonno Bassotto on 2010-02-25
> **Yuzem said:**
> I didn't do it that way because I didn't want to make those files available from the server and I really don't know what is the standard for web apps.


I think the standard for web apps is to store config data in the database itself, at least if it is user dependent. This would mean having users in the database, though, which is an additional layer of complexity which is totally not needed for Figuritas. It makes definitely more sense to use the system users, as you do now, since it is meant to be used locally.

Maybe the simplest solution (not the most elegant) would be to let the user provide the home path on the first launch and store it in a cookie.

By the way, why is that possible with thttpd?

---

### Post by Yuzem on 2010-02-25
> **Nonno Bassotto said:**
> By the way, why is that possible with thttpd?
I can't get $HOME from thttpd.
The only difference with thttpd is the location of the web app.

If figuritas is launched by the server it sets the config path one folder above the current folder ($PWD)
If it isn't launched by the server the config path is: ~/.figuritas

If the web path is ~/.figuritas/web then the config folder is the same in both cases and I can get $HOME from $PWD.

I think that I will need $HOME for example to be able to use the user config for mplayer or other apps.

---

### Post by micmic on 2010-02-25
> **Yuzem said:**
> Are you sure? It seems to work ok for me.
What is exactly the problem?
Could you tell me you bash version?
```
bash --version
```

Here you are:
```
GNU bash, versión 4.0.33(1)-release (i486-pc-linux-gnu)
```

My movies directory:
Movie1.avi
Movie2 with spaces.avi

When I run "figuritas movies -a /path2movies/*.avi", adds the Movie1 but there is nothing about "Movie2 with spaces"

---

### Post by Yuzem on 2010-02-25
I have tested it and it is working for me.
Can you try this:
```
for i in /path2movies/*.avi
{
    echo $i
}
```

If that command returns one movie by line you could try:
```
for i in /path2movies/*.avi
{
    figuritas movies -a "$i"
}
```

---

### Post by tariqf on 2010-03-01
I used this 

find /media/HITACHI/moveis/ -name *.avi -exec bash /usr/bin/figuritas movies -a {} \;



and managed to add nearly all my movies but it's very slow to add and I keep getting errors like this between successful additions


Error: near "s": syntax error


Any ideas anyone? Using 9.10 so I'm on bash 4.1 etc.

---

### Post by Yuzem on 2010-03-02
Ok, I think that I have found the problem. It wasn't caused by spaces but by single quotes.
It will be fixed in the next version, to fix it now:
```
sudo gedit /usr/share/figuritas/modules/movies.actions
```

Search for this line:
```
movies=($(sqlite "select movies from files where files = '$files'"))
```

Reeplace by:
```
movies=($(sqlite "select movies from files where files = '${files//\'/''}'"))
```

Now this one:
```
echo "delete from files where files = '$file';"
```

With this one:
```
echo "delete from files where files = '${file//\'/''}';"
```

---

### Post by tariqf on 2010-03-02
thanks for your quick response, seems to correct one problem but there exists another now! Adds them but lots of these.

Error: near line 8: column people is not unique
Error: near line 12: column characters is not unique
Error: near line 14: column people is not unique
Error: near line 35: column characters is not unique
Error: near line 37: column people is not unique
Error: near line 38: column characters is not unique
Error: near line 41: column characters is not unique
Error: near line 43: column people is not unique
Error: near line 47: column characters is not unique
Error: near line 49: column people is not unique

---

### Post by Yuzem on 2010-03-02
I can't reproduce the last one. It has no side effect, it means that you already have another movie with that character or person.
I tried importing three movies with same actors and characters but no error message...

---

### Post by tariqf on 2010-03-02
Ah ok. Also it stops indexing at 257 movies for some reason and no output to suggest why. Nomatter what I do I cannot add any more films after 257 are indexed!

---

### Post by Yuzem on 2010-03-02
Thats very strange, I have 1153 movies and I can add more.
Have you tried:
```
figuritas movies -a 'some title'
```

Maybe your hard drive is full:
```
df -h
```

---

### Post by tariqf on 2010-03-03
ok, I will check when I get back home. I did not realise the program copied movies anywhere I was assuming it just indexed them and kept the files in place! So if figuritas is copying all my movies from the USB drive I am scanning onto my HD that could explain it!

Thanks

---

### Post by Yuzem on 2010-03-03
> **tariqf said:**
> if figuritas is copying all my movies from the USB drive I am scanning onto my HD that could explain it!
No, it doesn't copy any movie, but it does save the covers, 2 images by movie (256px and 128px). It shouldn't use much space but if your HD was tight on space maybe it run out of it.

---

### Post by Yuzem on 2010-03-09
[There is a new version]("http://yuzem.blogspot.com/")

---

### Post by Yuzem on 2010-05-04
[There is a new version.]("http://yuzem.blogspot.com/search/label/Versions")

---

### Post by VCoolio on 2010-05-04
Awesome app, thanks! I also get a lot of the '*** is not unique' crap when adding stuff but it doesn't seem to break anything, so who cares. Maybe you could skip the prism dependency by opening localhost:port with the default browser or xdg-open or something? Or is there a reason to take prism, apart from it having no menus and toolbars that take screen estate?

---

### Post by Yuzem on 2010-05-05
> **VCoolio said:**
> Awesome app, thanks!
You are welcome! :)

> **VCoolio said:**
> I also get a lot of the '*** is not unique' crap when adding stuff but it doesn't seem to break anything
Yes, that shouldn't break anything but I will take a look.

> **VCoolio said:**
> Maybe you could skip the prism dependency by opening localhost:port with the default browser or xdg-open or something? Or is there a reason to take prism, apart from it having no menus and toolbars that take screen estate?
I use prism to make it look like a standard desktop application.  
I will make some changes to detect if prism is installed and if not use xdg-open but I see no reason to remove the prism dependence since it is almost always available.

---

### Post by VCoolio on 2010-05-06
Prism is fine, don't get me wrong, I just think apps should try to have as few dependencies as possible. 

Other thing though: there may be an issue with complex characters like é. For example try adding the movie matchstick men from imdb source and read the plot summary: it has the word protégé written with diamonds instead of é's on my pc.

---

### Post by Yuzem on 2010-05-06
That is strange, I have the same movie but it is looking fine here.
If you know how to use firebug, could you take a look at the code and tell me how it is written in the source?

---

### Post by VCoolio on 2010-05-07
> **Yuzem said:**
> That is strange, I have the same movie but it is looking fine here.
If you know how to use firebug, could you take a look at the code and tell me how it is written in the source?

Firebug also uses question marks inside diamonds. If you want to and know how to debug I'll help, but there may be too much variables to consider, like me using archlinux and a zsh shell. What do you recommend to open / read a .db file with by the way?

---

### Post by Yuzem on 2010-05-07
Yes, next step would be to check the database.
I use sqlitebrowser:
```
sqlitebrowser ~/.figuritas/movies.db
```

There is also an [extension for firefox.]("https://addons.mozilla.org/en-US/firefox/addon/5817")

Or try this command:
```
sqlite3 ~/.figuritas/movies.db 'select plot from movies where movies = "tt0325805"'
```

---

### Post by VCoolio on 2010-05-07
That was quick :). Sqlitebrowser has two dotted squares for each é. The sqlite3 command in urxvt did however print protégé correctly.

---

### Post by Yuzem on 2010-05-07
Ok, I think I found the problem.
The file gets downloaded correctly:
```
wget http://www.imdb.com/title/tt0325805/
```
The char is "&#xE9" which is correct.

I don't know why the sed decoding script doesn't work correctly:
```
sed index.html -f /usr/share/figuritas/html_decode.sed > index-decoded.html
```

The char decodes to "Ã©" when it clearly says é in the sed script.
I will check it later.

---

### Post by MadCookie on 2010-05-07
> **Yuzem said:**
> Figuritas is an open source multimedia manager for linux.

Description with screenshots:
[[IMG]http://3.bp.blogspot.com/_EbNPUgfUDXs/S35zizifkbI/AAAAAAAAAsI/imKgYBOPBIk/s320/figuritas-0.jpg[/IMG]]("http://yuzem.blogspot.com/p/figuritas.html")

I am opening this thread so anyone can report any problem here.
Comments, advices and requests are welcome.

Apple is gonna sue you for that layout :P

---

### Post by Yuzem on 2010-05-08
The bug is fixed.

> **MadCookie said:**
> Apple is gonna sue you for that layout :P
:lolflag: ...but seriously, I hope not to be infringing any copyright.

---

### Post by VCoolio on 2010-05-11
The special characters bug or the 'not unique' messages fixed? And where to get the fixed code? Thanks for working on it btw.

Also, is it me or doesn't localhost:9009 work in webkit? E.g. midori or [this](http://bbs.archlinux.org/viewtopic.php?id=96931)? Maybe you don't consider this an issue because you set it up to run in prism, which is ok then. Midori doesn't give an error message, but prispy says ```
** Message: console message: http://localhost:9009/web/script.js?5741 @917: SyntaxError: Parse error
``` Maybe that means something to you? 

Some little things I noticed while using it:
1. in genres, you see the 'see more' genre listed, but that's what imdb uses at the end of the genres line to link to more info on the genre. I think it should be skipped.
2. if you search something, the search limits if you browse further. Eg you search for 'black' and get movies containing black. Then, if you click actors, you only get actors containing black. Maybe it is meant as a feature? Then I'll have to remember to clean the search box.

---

### Post by Yuzem on 2010-05-11
> **VCoolio said:**
> The special characters bug or the 'not unique' messages fixed? And where to get the fixed code?
Yes, it is fixed. I will add a "test" branch in launchpad and post the link here.

> **VCoolio said:**
> Thanks for working on it btw.
Thanks for reporting. :)

> **VCoolio said:**
> Also, is it me or doesn't localhost:9009 work in webkit? E.g. midori or [this](http://bbs.archlinux.org/viewtopic.php?id=96931)? Maybe you don't consider this an issue because you set it up to run in prism, which is ok then. Midori doesn't give an error message, but prispy says ```
** Message: console message: http://localhost:9009/web/script.js?5741 @917: SyntaxError: Parse error
``` Maybe that means something to you? 
Actually on Midori if you use the "inpect element" tool, in the script tab, open the console and you should see an error message.
The error is probably due to missing semi-colons ";", maybe Midori and prispy use old webkit versions because it is working on chromium that uses webkit. The problem in chromium is the css code.
It is my intention to make it more compatible in the future.

> **VCoolio said:**
> Some little things I noticed while using it:
1. in genres, you see the 'see more' genre listed, but that's what imdb uses at the end of the genres line to link to more info on the genre. I think it should be skipped.
IMDB must have changed its html code. I will fix that.
Thanks again for reporting!

> **VCoolio said:**
> 2. if you search something, the search limits if you browse further. Eg you search for 'black' and get movies containing black. Then, if you click actors, you only get actors containing black. Maybe it is meant as a feature? Then I'll have to remember to clean the search box.
I'm aware of that behaviour but I'm not completely sure on how it should work since I will like to be able to search in the sidebar.

---

### Post by Yuzem on 2010-05-13
Well I ended up uploading it to the trunk series:
[https://launchpad.net/figuritas/+download]("https://launchpad.net/figuritas/+download")

fixed "not unique messages"
fixed encoding bug
updated IMDB grabber to fix genres bug

---

### Post by Yuzem on 2010-06-20
There is a [new version]("http://yuzem.blogspot.com/2010/06/version-006.html").

---

### Post by VCoolio on 2010-06-21
There is a dutch saying: if you're standing in the rain you get wet. So, while using figuritas, sometimes I add the wrong thing (because I need to rely on the covers in the 'add movies' dialog). The delete function doesn't work yet. No worries, you'd think, I'll use sqlite in the commandline. Now, I added [http://www.imdb.com/title/tt0247104/](http://www.imdb.com/title/tt0247104/) instead of [http://www.imdb.com/title/tt0119229/](http://www.imdb.com/title/tt0119229/). So, I open sqlite3 in a commandline:
```
sqlite3>select * from movies where movies='tt0247104';
movies|year|imdb_rating|votes|runtime|icon_width|icon_height|icon_alpha|icon_modified|name|type|plot|color
tt0247104|2000|8.1|345|30|187|256||2010-06-21+19:51:25.1374460620|"Grosse Pointe"|TV series 2000-2001|Satire centers on the off-camera antics of five actors who star in a fictional high school drama called "Grosse Pointe".|Color
```
Hurray, entry found. Now delete it:
```
sqlite3>delete from movies where movies='tt0247104';
Error: no such column: characters.movies
```
Now why does it come up with characters.movies, and why doesn't it just delete the stupid entry anyway?

Still, thanks for working on figuritas, it's very usable and fun!

---

### Post by Nonno Bassotto on 2010-06-21
Whenever I try to launch the new version of figuritas, either via CLI or with the menu entry, it spawns an ever growing number of processes, all called figuritas, which eat all the resources until I have to kill them.

---

### Post by Yuzem on 2010-06-22
> **VCoolio said:**
> because I need to rely on the covers in the 'add movies' dialog
If you click the cover it should open the IMDB page for the movie, that is new in the last version. Also if you leave the mouse hover the cover you should see a tool-tip with the title.

> **VCoolio said:**
> Now why does it come up with characters.movies, and why doesn't it just delete the stupid entry anyway?
When you add a movie a lot of entries get added in different tables (genres, directors, actors, characters, etc...) in order to maintain a clean database some triggers automatically delete those entries if you delete the movie but the movie should get deleted. Does it get deleted?
I will try to add the "remove movie" feature for the next version.

> **VCoolio said:**
> Still, thanks for working on figuritas, it's very usable and fun!
You are welcome! :D

> **Nonno Bassotto said:**
> Whenever I try to launch the new version of figuritas, either via CLI or with the menu entry, it spawns an ever growing number of processes, all called figuritas, which eat all the resources until I have to kill them.
I can't reproduce it.
Try deleting the config file "~/.figuritas/config"
If that doesn't work try deleting the config folder "~/.figuritas", you can move the database somewhere else and move it in again. You should also backup the cover's folder.
Have a terminal open with "killall figuritas" ready, just in case.

---

### Post by Nonno Bassotto on 2010-06-22
Removing .figuritas/config worked :-)

By the way, I have some other questions.

1) For me the star-rating is rather someUnknownJapaneseCharacter-rating. Which font should I install to make it work?

2) Figuritas does not keep the order I choose (by name). Is this a known bug?

3) Is there a way to manually change the title of a movie?

4) Is there a way to tell Figuritas to use italian names for the movies?

---

### Post by Yuzem on 2010-06-22
> 1) For me the star-rating is rather someUnknownJapaneseCharacter-rating. Which font should I install to make it work?
Actually I don't know, I have the same problem in my old computer in which I have Hardy installed but since it works ok in Lucid I thought that the fonts were available by default in Lucid.

You can try this:
```
sudo gedit /usr/share/figuritas/web/theme.css
```
Line 627 should be:
```
	font-size:2em;
```
Change it to:
```
	font-size:1.7em;
	letter-spacing:-0.3px;
```
Lines 651 and 652:
```
	content:'&#57880;&#57880;&#57880;&#57880;&#57880;';
/	content:'&#9733;&#9733;&#9733;&#9733;&#9733;';
```
to:
```
/	content:'&#57880;&#57880;&#57880;&#57880;&#57880;';
	content:'&#9733;&#9733;&#9733;&#9733;&#9733;';
```

> 2) Figuritas does not keep the order I choose (by name). Is this a known bug?
It is not implemented yet.

> 3) Is there a way to manually change the title of a movie?
Not yet, but it is planned. For now you can edit anything you want with sqlitebrowser:
```
sudo apt-get install sqlitebrowser
```
and:
```
sqlitebrowser ~/figuritas/config/movies.db
```

> 4) Is there a way to tell Figuritas to use italian names for the movies?
IMDB has recently changed the default title shown, it uses to show the original title so Italian movies got the Italian original title but now it gets the English one. It would be very easy to grab the original title again or to make it configurable but to get the Italian for all movies I don't know how, since the data seems not available on IMDB.

---

### Post by Shining Arcanine on 2010-06-22
> **Yuzem said:**
> Figuritas is an open source multimedia manager for linux.

Description with screenshots:
[[IMG]http://3.bp.blogspot.com/_EbNPUgfUDXs/S35zizifkbI/AAAAAAAAAsI/imKgYBOPBIk/s320/figuritas-0.jpg[/IMG]]("http://yuzem.blogspot.com/p/figuritas.html")

I am opening this thread so anyone can report any problem here.
Comments, advices and requests are welcome.
Is Figuritas a Latin word?

---

### Post by Nonno Bassotto on 2010-06-22
Thank you very much for all your replies. The change in CSS worked fine. :-D

By the way, how come you don't you know what font you are using? I do not understand. I mean, you visualize this character as a Japanese glyph in gedit, right?

As for the italian title, just point to the italian IMDB site, for instance
```

http://www.imdb.com/title/tt0050825/ -> Paths of Glory
http://www.imdb.it/title/tt0050825/ -> Orizzonti di gloria
http://www.imdb.fr/title/tt0050825/ -> Les sentiers de la gloire
http://www.imdb.es/title/tt0050825/ -> Senderos de gloria
http://www.imdb.de/title/tt0050825/ -> Wege zum Ruhm
http://www.imdb.pt/title/tt0050825/ -> Horizontes de Glória

```
and I guess it works for many other languages.

---

### Post by Yuzem on 2010-06-23
> **Shining Arcanine said:**
> Is Figuritas a Latin word?
I don't think so, in Argetnina "Album de figuritas" is equivalent to "Album de cromos" in Spain or "[Sticker Album]("http://www.meloncorp.com/sw/02/cromos_grande.jpg")" in english.
The literal translation would be "little figures".

> **Nonno Bassotto said:**
> Thank you very much for all your replies. The change in CSS worked fine. :-D
Great, I will use that then.

> **Nonno Bassotto said:**
> By the way, how come you don't you know what font you are using? I do not understand. I mean, you visualize this character as a Japanese glyph in gedit, right?
No, I see the star in gedit. The font that I'm using is sans-serif but the problem is that if I understand it correctly, if the char is not available in the specified font, it falls back to another font and I don't know in which font it is available.

> **Nonno Bassotto said:**
> As for the italian title, just point to the italian IMDB site, for instance
```

http://www.imdb.com/title/tt0050825/ -> Paths of Glory
http://www.imdb.it/title/tt0050825/ -> Orizzonti di gloria
http://www.imdb.fr/title/tt0050825/ -> Les sentiers de la gloire
http://www.imdb.es/title/tt0050825/ -> Senderos de gloria
http://www.imdb.de/title/tt0050825/ -> Wege zum Ruhm
http://www.imdb.pt/title/tt0050825/ -> Horizontes de Glória

```
and I guess it works for many other languages.
Ok, thanks, I will see if I can make it for the title and the plot.

---

### Post by VCoolio on 2010-06-23
> **Yuzem said:**
> When you add a movie a lot of entries get added in different tables (genres, directors, actors, characters, etc...) in order to maintain a clean database some triggers automatically delete those entries if you delete the movie but the movie should get deleted. Does it get deleted?
It doesn't get deleted, just that error. I also tried with sqlitebrowser; "browse data" tab, movies table, selected row and hit 'delete record' but no luck. No errors given either, just nothing.

> **Yuzem said:**
> 
I will try to add the "remove movie" feature for the next version.

I'll be patient, thanks.

---

### Post by Yuzem on 2010-06-23
> **VCoolio said:**
> It doesn't get deleted, just that error. I also tried with sqlitebrowser; "browse data" tab, movies table, selected row and hit 'delete record' but no luck. No errors given either, just nothing.

Ok, there is an problem with the triggers, it will be fixed for the next version.

---

### Post by ENigma885 on 2010-06-27
_@Yuzem_
[B]
Can u please provide a manual or a detailed how-to? I cannot get this to work basically!![/B]

I followed > **Yuzem said:**
> 
....

```
prism
```
in URL put localhost:9009
in Name: Figuritas
and check desktop
Click Ok and try to run figuritas.
You can delete the desktop shortcut after this.


I launched Figuritas afterwards, but I only get a blank page with no option to add any music or films library.

---

### Post by Yuzem on 2010-06-27
> **ENigma885 said:**
> I launched Figuritas afterwards, but I only get a blank page with no option to add any music or films library.
It is supposed to work without any extra steps. Install it and launch it.

Do you installed the last version (0.0.6)?
From which package, deb, rpm or tar?
Does it work on firefox?
Did you tried to run it from the application's menu or from the terminal?

Thanks for reporting the problem.

---

### Post by ENigma885 on 2010-06-27
**1-**> **Yuzem said:**
> 
Do you installed the last version (0.0.6)?
Yes, the latest version published [[COLOR="Blue"]here[/COLOR]]("http://launchpad.net/figuritas/trunk/0.0.6/+download/figuritas.0.0.6.deb") is installed. 

**2-**> **Yuzem said:**
> From which package, deb, rpm or tar?
deb
**3-**> **Yuzem said:**
> Does it work on firefox?
Do u mean Prism itself or Figuritas? Prism works fine when tested with real domains. If Figuritas, how to test that?
**4-**> **Yuzem said:**
> Did you tried to run it from the application's menu or from the terminal?
Applications menu (Applications>>Sound & Video)

---

### Post by Yuzem on 2010-06-28
> **ENigma885 said:**
> Do u mean Prism itself or Figuritas? Prism works fine when tested with real domains. If Figuritas, how to test that?
Open firefox and in the address bar type: [http://127.0.0.1:9009](http://127.0.0.1:9009)

> **ENigma885 said:**
> Applications menu (Applications>>Sound & Video)
Could you type this command and try again:
```
rm -r ~/.webapps/figuritas@prism.app
```

---

### Post by ENigma885 on 2010-06-28
> **Yuzem said:**
> Open firefox and in the address bar type: [http://127.0.0.1:9009](http://127.0.0.1:9009)

A blank page is displayed.

> **Yuzem said:**
> Could you type this command and try again:
```
rm -r ~/.webapps/figuritas@prism.app
```
Nothing changed.

Here's a screenshot in both Prism and FF.[[IMG]http://img641.imageshack.us/img641/3623/figuritas.th.png[/IMG]](http://img641.imageshack.us/i/figuritas.png/)

I am sure I'm missing something. A quick question; Figuritas is supposed to be a multimedia manager. So, how to configure it to the paths of the "multimedia" in my machine?

---

### Post by ENigma885 on 2010-06-28
*Mistakenly Double Posted*

---

### Post by Yuzem on 2010-06-28
> **ENigma885 said:**
> A blank page is displayed.
I really don't have a clue...
Do you have google chrome or chromium installed?
If yes could you try it there to go to: [http://127.0.0.1:9009](http://127.0.0.1:9009)

Could you tell me your firefox version:
```
firefox --version
```
And prism:
```
prism --version
```

> **ENigma885 said:**
> A quick question; Figuritas is supposed to be a multimedia manager. So, how to configure it to the paths of the "multimedia" in my machine?
Right now is not very "multi", only movies for the moment, you can add movies from any path recursively with:
```
figuritas movies -a path
```

If you want new movies on that path to be added automatically to figuritas you can do so with imdb-thumbnailer.

---

### Post by Yuzem on 2010-07-18
[There is a new version.]("http://yuzem.blogspot.com/2010/07/version-007.html")

---

### Post by VCoolio on 2010-07-20
[Tghis](http://tinyurl.com/2gyongx) is what I get with version 0.7 (the .tar version). Any idea what may be wrong? Thanks in advance.

---

### Post by Yuzem on 2010-07-20
> **VCoolio said:**
> [Tghis](http://tinyurl.com/2gyongx) is what I get with version 0.7 (the .tar version). Any idea what may be wrong? Thanks in advance.

It seems that the main css isn't applied. 
Try this on firefox:
[http://127.0.0.1:9009/web/theme.css]("http://127.0.0.1:9009/web/theme.css")

If you can see the file then open figuritas on firefox and with firebug check that the link to that css is present on the header.
It should look something like this:
```
<link rel="stylesheet" type="text/css" href="web/theme.css?9122">
```

If you can't see the file, check if exists, the location should be: ~/.figuritas/web/theme.css

If it exists maybe the permissions are wrong, it should be 644.

---

### Post by VCoolio on 2010-07-21
Thanks for trouble-shooting. The source for localhost:9009/# is:
[PHP]<html>/usr/share/figuritas/html: line 334: local: `http-equiv=content-type': not a valid identifier
<head><title>Figuritas</title><meta content="text/html; charset=UTF-8" http-equiv=""> <style type="text/css"> body:empty { background-image:url(web/theme/loading.png); background-position:center center; background-repeat:no-repeat; height:100%; } </style> <script src="web/jquery.js" type="text/javascript"></script><script src="web/script.js?4877" type="text/javascript"></script><link href="web/icons.css?4877" type="text/css" rel="stylesheet"><link href="web/theme.css?4877" type="text/css" rel="stylesheet"><link class="themes" id="gtk.css" href="web/appearance/themes/gtk.css?4877" type="text/css" rel="stylesheet"><link rel="shortcut icon" href="web/icons/favicon.ico" type="image/x-icon"><link rel="search" type="application/opensearchdescription+xml" title="Figuritas" href="web/opensearch"></head>
<body></body></html>[/PHP]
As you can see the number isn't 9122 but 4877. Is that wrong? Also there is an error at the top. The permissions on theme.css are 744 instead of 644, but that doesn't matter.

---

### Post by Yuzem on 2010-07-21
Sorry for the delay, I didn't get a notification. The number is fine, the problem seems to be the permissions.
Try this command:
```
chmod 644 ~/.figuritas/web/*.*
```

The error at the top should not make any difference but you can fix it anyway:
```
sudo gedit /usr/share/figuritas/html
```

Change line 599:
```
+ meta content="text/html; charset=UTF-8" http-equiv="content-type"
```

with this:
```
+ meta content="text/html; charset=UTF-8" #http-equiv="content-type"
```

What package did you installed?

---

### Post by VCoolio on 2010-07-22
Thank you, that was it after all. I already tried 644 on theme.css but I guess that didn't work because of httpd still running and remembering things. 
Ok, off to having fun with figuritas :). I installed [this](http://launchpad.net/figuritas/trunk/0.0.7/+download/figuritas.0.0.7.tar) by the way. 
Oh, and a little question: how do I start figuritas without prism launching? I'd like to access directly from my default web browser. 
Another question (sorry): do you happen to know what gtk widget I need to call to change the font color in the left pane? It's black on black for my theme. I could try to figure it out myself but if you know it that would be way faster. Maybe the black font is hardcoded in some figuritas file that I need to modify. Nice feature to use the gtk theme by the way. And thanks for implementing the delete function, that is going to be useful.

---

### Post by Yuzem on 2010-07-22
> **VCoolio said:**
> how do I start figuritas without prism launching? I'd like to access directly from my default web browser.

From gnome menu > System > Preferences > Startup session (or something like that)
Add: figuritas -S
That command launches thttpd for figuritas.

And click here: [http://127.0.0.1:9009]("http://127.0.0.1:9009")
Also, if prism is not installed figuritas should open in your default browser, right now it only works good on firefox.

> **VCoolio said:**
> Another question (sorry):
Its ok, ask as much as you want. ;)

> **VCoolio said:**
> do you happen to know what gtk widget I need to call to change the font color in the left pane? It's black on black for my theme.
Thats a bug. I tried [this theme]("http://lassekongo83.deviantart.com/art/Re-Crono-169044394?q=boost%3Apopular+in%3Acustomization%2Fskins%2Flinuxutil%2Fgnome%2Fgtk2&qo=35") and it seems that there are some things to adjust.

> **VCoolio said:**
> It's black on black for my theme. I could try to figure it out myself but if you know it that would be way faster.
And this way I can fix it, so thank for reporting. :)

> **VCoolio said:**
> Maybe the black font is hardcoded in some figuritas file that I need to modify.
Exactly, this should fix the sidebar problem:
```
gedit ~/.figuritas/web/appearance/themes/gtk.css
```

and add this somewhere:
```
.sidebar a {
	color:-moz-fieldtext !important;
}
```

> **VCoolio said:**
> Nice feature to use the gtk theme by the way. And thanks for implementing the delete function, that is going to be useful.
Thanks, and you are welcome!

---

### Post by Yuzem on 2010-07-24
[New version.]("http://yuzem.blogspot.com/2010/07/version-0071.html")

---

### Post by Nonno Bassotto on 2010-07-24
I don't know if you have a bug/feature tracker (of course Launchpad has one but it seems unused). So I will ask here.

A little glitch is the related to the infinite scrolling. When you reach the end of the movie list, the message
```

The database is empty. You can add movies from the menu, by clicking on the movies's tab.

```
appears. Another one is the fact that the folder public_html is created in my home every time I use figuritas. This may also create some problem for those people having that folder as the root of their site.

As for features, a most wanted one is the possibility to manually change the IMDB association. I added the movies on my hard disk with the command line, but some are not correctly associated. Ideally I would like to be able to enter the correct association (maybe giving the IMDB code) and all data (cover, actors, director, language and so on) should be changed. I don't think it is feasible to change all this data manually, while I think you already have the code written to obtain this data from the IMDB code.

---

### Post by Yuzem on 2010-07-24
> **Nonno Bassotto said:**
> A little glitch is the related to the infinite scrolling. When you reach the end of the movie list, the message
```
The database is empty. You can add movies from the menu, by clicking on the movies's tab.
```
appears. Another one is the fact that the folder public_html is created in my home every time I use figuritas. This may also create some problem for those people having that folder as the root of their site.
Ok, thanks for reporting, both bugs have been fixed.
[Re-download version 0.0.7.1]("https://launchpad.net/figuritas/+download") 

> **Nonno Bassotto said:**
> As for features, a most wanted one is the possibility to manually change the IMDB association. I added the movies on my hard disk with the command line, but some are not correctly associated. Ideally I would like to be able to enter the correct association (maybe giving the IMDB code) and all data (cover, actors, director, language and so on) should be changed. I don't think it is feasible to change all this data manually, while I think you already have the code written to obtain this data from the IMDB code.
Yes, thats why I have imdb-thumbnailer settled to bind only.
If you already have the code you could remove the movie and add the correct one, then drag and drop the movie file to the added movie in figuritas to associate it (not implemented).

For the moment you can use sqlitebrowser to insert the movie path or imdb-thumbnailer with the --name flag:
```
imdb-thumbnailer --name "path/2/unrecognized-movie" "title"
```
Then you only have to remove the wrong movie.

Anyway I will soon announce the figuritas's uservoice.com forum so anyone will be able to submit ideas and vote for them.

---

### Post by Nonno Bassotto on 2010-07-25
Thank you very much for correcting the bugs so quickly!

I have tried to add movies the ways you told me. Using sqlite was a little uncomfortable, since one also has to add manually the "modified" and "size" fields. I have not been able to make imdb-thumbnailer work. I have tried for instance
```

imdb-thumbnailer --name "/media/disk/Film/L'apparenza inganna.avi" "The Closet"

```
```

imdb-thumbnailer --name "/media/disk/Film/L'apparenza inganna.avi" "The c
closet"

```
```

imdb-thumbnailer --name "/media/disk/Film/L'apparenza inganna.avi" "Le placard"

```

and in no case I was able to get the file associated with the movie (the title of the movie on Figuritas is "The Closet", but I was not sure whether it would reload the info from IMDB, so I tried the original title too).

---

### Post by Yuzem on 2010-07-25
> **Nonno Bassotto said:**
> I have not been able to make imdb-thumbnailer work.

I tried:
```
imdb-thumbnailer --name '/home/azd/Films/  L'\''apparenza inganna.avi' "Le placard"
```
And it worked, could it be that your file manager didn't update the thumbnail correctly?
It helps to identify the movie correctly if you put more information on the file names like the year (2001).

Maybe I should add and option in imdb-thumbnailer to specify the language but I don't know if it will work well if the title is not in the specifed language.

If you want to try it for italian:
```
sudo gedit /usr/bin/imdb-thumbnailer
```

Replace line 399:
```
id=$(wget -U firefox -qO - "http://www.google.com/search?hl=en&q=site%3Aimdb.com%2Ftitle+$query" | sed 's/>/\n/g' | grep -m 1 '<a href="http://www.imdb.com/title')
```
with:
```
id=$(wget -U firefox -qO - "http://www.google.com/search?hl=en&q=site%3Aimdb.it%2Ftitle+$query" | sed 's/>/\n/g' | grep -m 1 '<a href="http://www.imdb.com/title')
```

> **Nonno Bassotto said:**
> and in no case I was able to get the file associated with the movie
Yes you are right, it seems that the movie doesn't get associated.

> **Nonno Bassotto said:**
> the title of the movie on Figuritas is "The Closet"
Did you added the movie after version 0.0.7?
If yes then the title and the plot should be in italian or there may be a bug.

I will add an option to figuritas to associate files from the command line.

---

### Post by Nonno Bassotto on 2010-07-25
I am a bit confused. I used imdb-thumbnailer with the figuritas=bind option. I was trying to associate the file with the movie in figuritas, not to get a thumbnail in Nautilus.

As for movies, I get the italian information when adding them in batch mode from files, but the English information when adding them manually from Figuritas.

---

### Post by Yuzem on 2010-07-25
> **Nonno Bassotto said:**
> I am a bit confused. I used imdb-thumbnailer with the figuritas=bind option. I was trying to associate the file with the movie in figuritas, not to get a thumbnail in Nautilus.
Ok, I misunderstood you.

> **Nonno Bassotto said:**
> As for movies, I get the italian information when adding them in batch mode from files, but the English information when adding them manually from Figuritas.
When executed from the command line figuritas uses the $LANG variable but in gui mode it uses $HTTP_ACCEPT_LANGUAGE because $LANG is not available, I think that you can add it to the config to solve the problem.

gedit ~/.figuritas/config
add: LANG=it

---

### Post by Nonno Bassotto on 2010-07-26
Thank you, using the config works. :p Anyway my HTTP_ACCEPT_LANGUAGE is
```

it,en-us;q=0.7,en;q=0.3

```

I report two more bugs:

1) After adding a movie, the infinite scrolling does not work anymore. It looks like you are already at the end of the list, even if you are not.

2) Often clicking on a link brings you to some web page, and there is no way to go back (in Prism).

---

### Post by Yuzem on 2010-07-26
> **Nonno Bassotto said:**
> Thank you, using the config works. :p Anyway my HTTP_ACCEPT_LANGUAGE is
```

it,en-us;q=0.7,en;q=0.3

```
Thats strange, the first is used, I have no idea why it isn't working on your computer.

> **Nonno Bassotto said:**
> I report two more bugs:

1) After adding a movie, the infinite scrolling does not work anymore. It looks like you are already at the end of the list, even if you are not.

2) Often clicking on a link brings you to some web page, and there is no way to go back (in Prism).
Thanks for reporting, both bugs will be fixed in version 0.0.7.2
Let me know if there is any other bug.

---

### Post by Yuzem on 2010-07-28
New version:
```
Fixed infinite scroll after adding movies.
Fixed triggers (again).
Fixed links loading in current window (prism).
Added option: --bind id file.
```

[Download]("https://launchpad.net/figuritas/trunk/0.0.7.2")

Please report any problem.

---

### Post by Yuzem on 2010-08-02
Here it is the uservoice acount to vote, comment and submit ideas:
[http://figuritas.uservoice.com]("http://figuritas.uservoice.com")

---

### Post by Nonno Bassotto on 2010-08-02
I have used my votes :-) By the way, should we still use the forum for bugs? Uservoice does not seem really suitable for that, as there are only 10 points per user.

---

### Post by Yuzem on 2010-08-02
You can report bugs in [launchpad]("https://bugs.launchpad.net/figuritas"), I am subscribed so I should get notified but it is ok if you want to use the forum or report it in the blog version entry.

If you run out of votes and you have and idea, there is a trick, take away one vote from another idea and use it to submit the new idea, then you can take away the vote from the new idea, other people may vote for it.
Thats how I submitted all the ideas, I have also 10 votes.

---

### Post by Nonno Bassotto on 2010-08-22
I think I should mention the [poll by Yuzem]("http://ubuntuforums.org/showthread.php?t=1558438") about the Figuritas add-on for Firefox.

---

### Post by earthpigg on 2010-08-22
hi,

using .7.2, just installed it.

got prism to stfu by doing the localhost thing mentioned way earlier in the thread.

having problems adding movies. it detects the frew that happen to be in ~/Downloads, but not the ones in ~/Videos/Movies.

this did not do the trick:

> figuritas movies -a ~/Video/Movies/*.avi

---

### Post by Yuzem on 2010-08-22
```
I think I should mention the poll by Yuzem about the Figuritas add-on for Firefox.
```
Thanks Nonno!

> **earthpigg said:**
> got prism to stfu by doing the localhost thing mentioned way earlier in the thread.
Are you saying that it didn't worked at first try?

> **earthpigg said:**
> having problems adding movies. it detects the frew that happen to be in ~/Downloads, but not the ones in ~/Videos/Movies

Did it gave you any output?
Maybe the path that didn't worked is a symbolic link:
stat ~/Videos/Movies

You could try with this command and post the output:
```
bash -x figuritas movies -a ~/Video/Movies/*.avi 
```

It should give you a long output.

---

### Post by earthpigg on 2010-08-22
hi,

no, the original command gave no output.

this command:

```
bash -x figuritas movies -a ~/Video/Movies/*.avi
```

does indeed give very long output. here's the tail end of it, over the 2,000 lines i have as my scrollback threshold. if you want all lines, i can provide that as well.

```
+ read -d '<' E C
+ [[ a href="/support/websearch/bin/answer.py?answer=134479&amp;hl=en" class=fl = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ /a = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ a href="/quality_form?q=site:imdb.com/title+/home/chris/Video/Movies/*.avi&amp;hl=en&amp;ie=UTF-8" target=_blank class=fl = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ /a = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ /div = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ div id=fll style="margin:19px auto 19px auto;text-align:center" = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ a href="/" = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ /a = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ a href="/intl/en/ads/" = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ /a = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ a href="/services/" = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ /a = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ a href="/intl/en/privacy.html" = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ /a = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ a href="/intl/en/about.html" = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ /a = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ /div = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ /div = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ /div = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ textarea style="display:none" id=hcache = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ /textarea = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ div id=xjsd = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ /div = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ div id=xjsi = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ script = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ /script = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ /div = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ script = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ [[ b;++j){k=i[j];if(k.complete||typeof k.src!="string"||!k.src)++d;else if(k.addEventListener){k.addEventListener("load",h,false);k.addEventListener("error",
h,false)}else{k.attachEvent("onload",h);k.attachEvent("onerror",h)}}e=b-d;function l(){if(!google.timers.load.t)return;google.timers.load.t.ol=(new Date).getTime();google.timers.load.t.iml=f;google.kCSI.imc=d;google.kCSI.imn=b;google.kCSI.imp=e;google.timers.load.t.xjs&&google.report&&google.report(google.timers.load,google.kCSI)}if(window.addEventListener)window.addEventListener("load",l,false);else if(window.attachEvent)window.attachEvent("onload",l);google.timers.load.t.prt=(f=(new Date).getTime());
})();
 = h3* ]]
+ rdom
+ local 'IFS=>'
+ read -d '<' E C
+ select movie in '"${name[@]}"'
+ exit
[chris: ~]$

```


one more thing is that it doesn't seem to remember the 8 movies. i have to add them over again every time i start it. i do have full read/write permissions of ~/.figuritas & haven't manually modified any files in that folder, or the folder itself.

---

### Post by Yuzem on 2010-08-22
> **earthpigg said:**
> one more thing is that it doesn't seem to remember the 8 movies. i have to add them over again every time i start it. i do have full read/write permissions of ~/.figuritas & haven't manually modified any files in that folder, or the folder itself.
That is very strange, does the movies get remembered if you add them with the url?:
```
figuritas movies -a http://imdb.com/...
```

Looking at the output it seems that the shell isn't expanding the asterisk, try this:
```
for i in ~/Video/Movies/*.avi; do echo $i ; done
```
If your movies get listed then try this:
```
for i in ~/Video/Movies/*.avi; do figuritas movies -a "$i" ; done
```

---

### Post by earthpigg on 2010-08-22
```
[chris: ~]$ for i in ~/Videos/Movies/*.avi; do figuritas movies -a "$i" ; done
Error: near line 1: database is locked
added: tt0120586 American History X (1998)
tt0120586: /home/chris/Videos/Movies/American History X.avi
Error: near line 1: database is locked
added: tt0800308 Appaloosa (2008)
tt0800308: /home/chris/Videos/Movies/Appaloosa.avi
[chris: ~]$ 
```

and then it shows those two movies.

a third movie had some unusual characters in it. parenthesis and an apostrophe. renaming it allowed it to be added.


any way to add them recursively? ie: to include any subdirectories found

also: any way to locate and strip away unusual characters? that would qualify as a potential feature request, if you are up to it.

---

### Post by Yuzem on 2010-08-22
> **earthpigg said:**
> any way to add them recursively? ie: to include any subdirectories found
It should work recursively with a folder by default:
```
figuritas movies -a ~/Videos/Movies
```

> **earthpigg said:**
> also: any way to locate and strip away unusual characters? that would qualify as a potential feature request, if you are up to it.
Unusual characters shouldn't be a problem at all, maybe there is a bug, I will take a look.

---

### Post by Yuzem on 2010-08-28
Hi, I'am uploading a beta version for testing, there are a lot of changes, fixes and new features in this version so please report any problem.

```
Added nested browsers (multiple browsers in the sidebar).
Moved filters panel to browsers.
Security fix.
Changed favicon.
Added flag -r id rating.
Some work on editing data.
Removed control panel.
Added flag module.db.
Basic support for playing over the network (mplayer).
New hotkeys, see the help page.
Changes in filters, query and tabs.
Fixed search bug when searching multiple times.
Fixed playing from subtitles tab.
Removed Appearance tab and added theme option.
Fixed wrong language detection.
Localized imdb links.
Added basic support for translations.
Fixed: database is locked.
Speedup on adding movies.
New options movie_player and sidebarWidth.
Fixed false new version alert.
Lots of internal changes.
```

Translation are not perfect, it is possible to translate genres and other data, this needs some work.
Translation files are in:
/usr/share/figuritas/translations

The most important feature added is nested browsers, it is very simple and powerful concept: You open a browser, select an item and then you can select another browser, the previous one gets collapsed.

Enjoy!

[https://launchpad.net/figuritas/testing/0.0.8]("https://launchpad.net/figuritas/testing/0.0.8")

---

### Post by Nonno Bassotto on 2010-08-29
Hi Yuzem, I'm not sure I will be able to try it out, since I do not have access to my computer for a couple of weeks. So, for the extension, you will have to wait. :-(

---

### Post by Yuzem on 2010-08-29
Ok Nonno, thanks for letting me know.

---

### Post by VCoolio on 2010-08-29
> **Yuzem said:**
> Hi, I'am uploading a beta version for testing, there are a lot of changes, fixes and new features in this version so please report any problem.

OK: 
- top left above the Movies button, I get "/usr/share/figuritas/html.sh: line 397: tr: bad array subscript browsers
- when I click a movie or a person, no details on the bottom half: it keeps saying "loading..." and code like: ```
+ menu tabs + menu=() + local menu name href i j opts IFS class=menu liclass + [[ tabs = context ]] + + div class=menu id=tabs + local 'v='
+ [[ -n '' ]] + + span class=arrow + local 'v=' + - span + echo -n '' + + ul + local 'v=

      '
          o + for i in '"$@"' + [[ tabs = .* ]] + menu_tabs + local name + set -- details '?module=movies&tab=details,movies,tt0114214' scenes '?module=movies&tab=scenes,movies,tt0114214' trailer '?module=movies&tab=trailer,movies,tt0114214' explore '?module=movies&tab=explore,movies,tt0114214' + shift 2 + [[ -n scenes ]] + name=scenes + echo -n 'Scenes
          o ' Scenes
          o + shift + shift + [[ -n trailer ]] + name=trailer + echo -n 'Trailer
          o ' Trailer
          o + shift + shift + [[ -n explore ]] + name=explore + echo -n 'Explore
          o ' Explore
            + shift + shift + [[ -n '' ]] + [[ -n '' ]] + - ul + echo -n '' 

+ - div + echo -n '
'
+ set +x 
```
Screenshot: [[img]http://omploader.org/tNWRsNw[/img]](http://omploader.org/vNWRsNw)

---

### Post by Yuzem on 2010-08-29
I can't reproduce it but try this:
```
gedit /usr/share/figuritas/html.sh
```

Remove line 707 and 709:
```
set -x
```
and
```
set +x
```

Now in line 397:
```
echo ${tr[$name]:-${name:-${tr[$1]:-$1}}}
```
Change it to:
```
[[ $name ]] || name=$1
echo ${tr[$name]:-$name}
```

---

### Post by VCoolio on 2010-08-29
Wow. That indeed fixed those issues, awesome. There is still the big black bar between top and bottom half. You can see that also in the screenshot I posted; I hadn't noticed yet. May also have to do with the black gtk theme. I haven't really tested much, the issues I had were easily spot. If there is more I'll let you know. Thanks for developing. 
Is there a usable addon already to be combined with imdb or are you waiting for the poll to have statistically usable results?

---

### Post by Yuzem on 2010-08-29
> **VCoolio said:**
> There is still the big black bar between top and bottom half.
Try to download again from this link:
[https://launchpad.net/figuritas/testing/0.0.8]("https://launchpad.net/figuritas/testing/0.0.8")

> **VCoolio said:**
> If there is more I'll let you know.
Thanks.

> **VCoolio said:**
> Is there a usable addon already to be combined with imdb or are you waiting for the poll to have statistically usable results?
I think Nonno should answer this.

---

### Post by Nonno Bassotto on 2010-08-30
> **VCoolio said:**
> Is there a usable addon already to be combined with imdb or are you waiting for the poll to have statistically usable results?

Yes, there is a usable add-on. At least, it would work with the partially updated versions of Figuritas that Yuzem sent me these days. I do not have a way to test it with 0.0.8 right now.

I attach it here; because of limitations of Ubuntuforums, I had to rename it as .zip. Just download it, rename it as .xpi and install it.

Let me know what you think, in particular if you have problems. Once I test with 0.0.8 and have the final results from the poll, I will upload an updated version.

---

### Post by VCoolio on 2010-08-30
> **Nonno Bassotto said:**
> Let me know what you think, in particular if you have problems. Once I test with 0.0.8 and have the final results from the poll, I will upload an updated version.

Hm, I added it in firefox 3.6.8 with figuritas 0.0.8, I didn't get an icon. So I can't use it. Anyway, I always use conkeror so I've established a keybinding to issue 'figuritas movies -a' on the imdb page I'm currently on :popcorn:

@Yuzem: the black bar is gone with the 'new' 0.0.8. Another issue though: when I select a movie, I get a lot of these errors in the 'characters' column (in some movies all of them, in some just a few or even none, I don't see a pattern yet): ```
index.cgi: line 361: tr: bad array subscript
```

Thanks to both for improvements. 

If someone cares for a howto to get a keybinding in conkeror:
1. Create a file /usr/bin/imdb with permission 755 containing: ```
#!/bin/sh
figuritas movies -a $*
``` or do something else so your $SHELL recognizes the 'imdb' command as being "figuritas movies -a $*".
2. Add to your conkeror config (credits to retroj in #conkeror): ```
interactive("shell-command-on-current-url", null, "shell-command-on-url",
        $browser_object = function (I) I.buffer.current_uri.spec);
define_key(default_global_keymap, "I", "shell-command-on-current-url");
```
3. When you're on the imdb page of your movie, hit 'I' (shift-i), then enter 'imdb'.

---

### Post by Nonno Bassotto on 2010-08-31
> **VCoolio said:**
> Hm, I added it in firefox 3.6.8 with figuritas 0.0.8, I didn't get an icon. So I can't use it.

Have you tried going to a IMDB page? The icon should appear. By default the icon is not always present, but you can change that in the preferences.

---

### Post by Yuzem on 2010-08-31
> **VCoolio said:**
> Another issue though: when I select a movie, I get a lot of these errors in the 'characters' column (in some movies all of them, in some just a few or even none, I don't see a pattern yet): ```
index.cgi: line 361: tr: bad array subscript
```

Ok it should be fixed now, also now it is possible to edit movie information if you want to test it:
[https://launchpad.net/figuritas/testing/0.0.8]("https://launchpad.net/figuritas/testing/0.0.8")

---

### Post by Nonno Bassotto on 2010-09-07
I have tried the new version. Finally we have editable titles! :-D

I will upload a working version of the Firefox add-on soon.

---

### Post by Nonno Bassotto on 2010-09-07
There are some bugs in the new version:

1) When I play a movie from Figuritas, nothing happens
2) When removing a movie, an error message appears stating that it is not possible to remove a couple of JPGs
3) When adding a movie, the error
```

/usr/share/figuritas/html.sh: line 730: tab_add: command not found /usr/share/figuritas/html.sh: line 732: tr: bad array subscript

```
appears, and the loading icon stays there forever.

---

### Post by Yuzem on 2010-09-08
Ok, Nonno, thank you very much.

I think all bugs should have been fixed now:
[https://launchpad.net/figuritas/testing/0.0.8]("https://launchpad.net/figuritas/testing/0.0.8")

---

### Post by Nonno Bassotto on 2010-09-08
Thank you, the bugs seem fixed now.

I have updated the add-on for Firefox. You can find it [here]("http://projects.andreaferretti.it/files/figuritas.xpi").

---

### Post by ElJefeRocks on 2010-10-24
This program is just what I was looking for! Amazing work on this.

One problem I have encountered is that I cannot add more than 256 movies.  Is this a limitation in the figuritas or sqlite database?  I searched around but couldn't find anything relating to this.  I am on lucidx64.

---

### Post by Yuzem on 2010-10-24
> **ElJefeRocks said:**
> This program is just what I was looking for! Amazing work on this.
Thanks. :)

> **ElJefeRocks said:**
> One problem I have encountered is that I cannot add more than 256 movies.  Is this a limitation in the figuritas or sqlite database?  I searched around but couldn't find anything relating to this.  I am on lucidx64.
That is very strange, it is not a limitation, I have currently 1238 movies.
Try this at the command line:
> killall figuritas
killall sqlite3
And try again.

---

### Post by ElJefeRocks on 2010-10-24
Thanks Yuzem.  I restarted and added the files a letter at a time (figuritas -a /media/directory/A*.avi) and it worked. :)

---

### Post by VCoolio on 2010-11-23
Sorry to bother again, but I have an issue with 0.0.8.2 on a new installation (I copied the .figuritas folder over):
- minor: in the title bar it shows an icon that an update is available as it claims to be version 0.0.7.2
- major: when I click a movie, the lower half stays empty with a 'loading...' thingy in between; if I click the movie poster in the top half, a second 'loading...' thingy appears, still nothing in the lower half, not even error output. The same with 0.0.8 by the way, I tried a little downgrading. So is it me, or is it imdb.com (I'm not sure if those details are retrieved live from imdb.com or also from the database, but imdb.com has changed a lot lately)? Any suggestions appreciated, as always.

---

### Post by Yuzem on 2010-11-23
> **VCoolio said:**
> Sorry to bother again
Nothing like that. :)

Try this and post the output:
```
cat ~/.figuritas/config
```
And this:
```
figuritas --version
```
Did you tried it in firefox?

> I'm not sure if those details are retrieved live from imdb.com or also from the database
Not from imdb, only from the database.

---

### Post by VCoolio on 2010-11-24
I downloaded 0.0.8.2 (at least it says it's that) [here](http://launchpadlibrarian.net/57095260/figuritas.0.0.8.2.tar).
figuritas --version says: 0.0.7.2

Minefield 4.0b8pre has the same issue. I'm using conkeror which uses xulrunner2.0b8pre, same issue of course.
Just to be sure I also installed firefox 3.6.12 with xulrunner-1.9.2.12, and there it works! There are a lot of changes in firefox/xulrunner going to version 4 and 2, so once they are released I think you'll have to update some of the code.

Thanks for the hint on firefox (I remember now you've told me or others the same earlier, but I didn't think of that). Now I'm going to see if a more lightweight browser wants to run figuritas for me (prism doesn't seem to work on 64-bit systems).

Edit: I see now in .config that it mentions the version number. I moved it, restarted figuritas and now it says it is 0.0.8.2. Solved. Maybe you should have figuritas echo it's real version into the config file on each launch? Or not get the version number from a user config file at all.

---

### Post by VCoolio on 2010-11-24
For some reason I can't edit my previous post, so a new one. I see now in .config that it mentions the version number. Remembering I copied this folder over from my old pc I moved it, restarted figuritas and now it says it is 0.0.8.2. Solved. Maybe you should have figuritas echo it's real version into the config file on each launch? Or not get the version number from a user config file at all.

---

### Post by VCoolio on 2010-11-24
For some reason I can't edit my previous post, so a new one. I see now in .config that it mentions the version number. Remembering I copied this folder over from my old pc I moved it, restarted figuritas and now it says it is 0.0.8.2. Solved. Maybe you should have figuritas echo it's real version into the config file on each launch? Or not get the version number from a user config file at all.

---

### Post by Yuzem on 2010-11-24
> Now I'm going to see if a more lightweight browser wants to run figuritas for me (prism doesn't seem to work on 64-bit systems).
You can try:
```
figuritas --python
```
It doesn't work well with external links but that will be fixed in the next version.

> Maybe you should have figuritas echo it's real version into the config file on each launch?
I took a look at the code and it is a bug, version 0.0.8.4 uses $config_version in the config and $version in the application, the problem is that $version wasn't removed from the config.

---

### Post by Yuzem on 2011-03-01
Hi everybody, there is new version.

**Improvements:**
The main toolbar now works like tabs.
The welcome page has been redesigned.
Add/scan movie folder gui dialog.
Improved section files.
Bind movies even if they are not in figuritas.
Counts in filters.
Update icons when some changes occur.
Links to IMDb, youtube and amazon.
Added support for iso and wmv files.
Auto-update some data like votes and rating.
Improved drag and drop.
Associate movies and files by drag and drop (from inside figuritas).
Super fast sections counts.

**Changes:**
Open external links in default browser.
Tables movies and user are now one table.
Sql limit changed from 25 to 50.
Speedup retrieving of movies.
Modules are now called libraries and browsers are called sections.
Removed --bind flag.
Removed gtk-frame theme.

**Fixes:**
Workaround firefox bug with contentEditable and middle clicks.
Fixed character grabbing.
Fixed random high cpu usage.
Fixed errors when adding movies.

Other changes.

[Download]("https://launchpad.net/figuritas/+download")

---

### Post by VCoolio on 2011-03-02
Nice to see there's new stuff! Thanks again. Figuritas was a little broken for me because it wouldn't show the lower pane with movie info. Now it's back in business.

---

### Post by Nonno Bassotto on 2011-03-05
The last update broke Figuritas for me. I get
```
Error: near line 3: no such column: on_disk
```
and my movies library is now empty. Similarly in the Sections tab I have the message
```
Error: no such table: sections_count
```
Moreover, the program reports to be version 0.0.7.2 instead of 0.0.9

---

### Post by Yuzem on 2011-03-06
> and my movies library is now empty. Similarly in the Sections tab I have the message

Don't worry, your movies should be there, please tell me the result of this commands:

```
sqlite3 ~/.figuritas/movies.db 'select count(*) from movies'
```
```
sqlite3 ~/.figuritas/movies.db 'select count(*) from _movies'
```
```
sqlite3 ~/.figuritas/movies.db 'select * from options'
```
```
sqlite3 ~/.figuritas/movies.db.backup 'select count(*) from movies'
```
```
cat ~/.figuritas/config
```

---

### Post by Nonno Bassotto on 2011-03-06
Here they are, in order:

```
248
```
```
Error: no such table: _movies
```
```
Error: no such table: options
```
```
Error: no such table: movies
```
```
version=0.0.7.2
last_version=0.0.9
last_version_check=2011-03-06
LANG=it
appearance=(themes/gtk.css)
config_version=0.0.7.2
movie_folder=/media/disk/Film
```

---

### Post by Yuzem on 2011-03-06
I'm thinking that maybe you can solve the problem by setting this:
```
config_version=0.0.8
```
and remove:
```
version=0.0.7.2
```

in:
```
~/.figuritas/config
```

---

### Post by Nonno Bassotto on 2011-03-06
Thank you, that solved my problems! :-)

---

### Post by BULLIT22 on 2011-10-27
Hey there, 

I've been looking for a Linux tool like this for awhile now. Looks great, Although, I can't seem to add a directory nor run Figuritas in Firefox. When started from Firefox, I just see a gray bar at the top and a spinning loading thing that never goes away. When launched from Sound and Video menu it seems to start fine but then I try and add a drives folder full of movies and I get this "error: folder does not exist". Any suggestions as to what I may need to do?

Path to movies is,

/media/Movies 2/New Rips/

Thanks in advance.

---

### Post by Yuzem on 2011-10-27
Hi BULLIT22!

Before running figuritas from Firefox you must run it as a server:
```
figuritsa -S
```
Then see if it works in Firefox. You can add that command to your application startup list.

I think the problem with your movie path is the spaces, try this:
```
gedit .figuritas/config
```
Add this line and delete the older:
```
movies_folder="/media/Movies 2/New Rips"
```

---

### Post by BULLIT22 on 2011-10-28
Thanks, I'll give it a go when I get home.

---


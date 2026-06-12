---
title: "ubuntu users' packages website"
date: 2004-10-27
forum: The Cafe
---

### Post by im_ka on 2004-10-27
hello deb builders!

i've seen some deb packages being offered on this forum.
how about dedicating a website to these unofficial packages? i've got enough webspace on my university's server. 
i could set up a simple website, all you need to do is upload the debs.

what do you think?

---

### Post by oddabe19 on 2004-10-27
I'm game.
I would set it up via FTP though, because if you allow anyone to throw anything in there, there could be multiple problems. Or password the upload or something and only allow trusted people to upload their .debs.
Right now, i store my .debs on my comcast server... yeah... right, that'll last about 2 more .debs.

I'm up for that idea.... you're a smart man. Hats off to you.

---

### Post by im_ka on 2004-10-27
i can't set up ftp, and i can't protect it with password. just checked, and it's only www/html (no php, sql ,etc.).

the best thing we can do is to use my gmail account (1gb storage). just send files to ikalomista[at]gmail[dot]com and i'll take care of the rest. of course, deb's linked on the forum don't need to be mailed to me.
if someone can and want to do it more professionaly, please raise your vioce :)

allright, what i need is:

-the deb file (duuh :)) with a short description. the filename should include the version nr.
-name that should appear on the website
-valid email adress (for possible bugreports)

did i forget anything?

---

### Post by oddabe19 on 2004-10-27
I have gmail too, but iirc, they only allow a 10mb transfer, so if the deb is bigger, you're kinda screwed.  My server is on loan, or else, i would set up a FTP upload server.... Maybe someone else has some extra space.

---

### Post by im_ka on 2004-10-27
[QUOTE=oddabe19]I have gmail too, but iirc, they only allow a 10mb transfer, so if the deb is bigger, you're kinda screwed.  My server is on loan, or else, i would set up a FTP upload server.... Maybe someone else has some extra space.[/QUOTE]

let's see what the possibilites are. i might be able to set up a folder on my college account with password. if not, i can still apply for additional services. but i'll have to hand in a real application for that (for what i want to use it, etc.) and it`ll take some time til they decide whether i get the space or not. i know they're unix friendly (university of vienna is on freebsd).

anyone else?

---

### Post by im_ka on 2004-10-27
it's not possible to set up a folder with different permissions, i log in with a password myself.

is there any1 who's got the needed "infrastructure"?
if not, i'll apply for additional services + server space.

coders are also welcome to help me ;)

---

### Post by nuopus on 2004-10-28
[QUOTE=im_ka]hello deb builders!

i've seen some deb packages being offered on this forum.
how about dedicating a website to these unofficial packages? i've got enough webspace on my university's server. 
i could set up a simple website, all you need to do is upload the debs.

what do you think?[/QUOTE]
 Ya thats a good idea. The problem I am having with my debs are the ubuntu repos keep wanting to downgrade and I think I know why. Mine is gaim-1.0.2 with 1.0.2 as version number from the source. But .. the one in Ubuntu is 1:1.0. I am thinking that apt thinks 1:1.0 is higher than 1.0.2. Oh well .. ... anyone have a clue on what is going on?

---

### Post by im_ka on 2004-10-28
i don't have experience with deb-building, sorry.

is there any interest?

---

### Post by jdodson on 2004-10-28
i have a university account that does allow for php/mysql as i use it on my page @ [http://cs.georgefox.edu/~jdodson](http://cs.georgefox.edu/~jdodson)  if you need any space or dynamic/password stuff, let me know.

---

### Post by im_ka on 2004-10-28
that would be great!

i don't know php/mysql YET :) but i guess i could start without and learn it while the number of packages grow (basically, i wanna enable searching by package name/author/date/etc.)

---

### Post by jdodson on 2004-10-28
ok cool.  though i have the reverse problem, i have php/mysql access but limited storage :-o 

not sure if that helps.  

however i would consider getting some server space(and paying for it) to host these .debs if the community finds them useful.

-jon

---

### Post by im_ka on 2004-10-28
i can get additional space from my university. it's just an official procedure i guess, i need to apply for it.

we could use your space for "incoming", and move the files over to my space = 200 mb at the moment... should be enough for a start.

---

### Post by jdodson on 2004-10-28
i dig.  ok so, hmm i wonder how we would want to set everything up....

---

### Post by im_ka on 2004-10-28
my idea:

set up a folder where people can upload their files to. call it "incoming" or something. i can then grab the files from there and put it on my webspace... 

bit compicated, but i don't think that there'll be much to upload at the beginning. and i'll apply for additional server space with php/sql as we grow.

i'll be gone for the week-end, i can probably dig into it sunday night.

---

### Post by jdodson on 2004-10-28
ok.  i think i might have some time next week to implement that.  i could create an admin interface that you could pull the info from.  i will attempt to harminoize the look and feel with that of the ubuntu community(dark brown/light brown colors).

-jon :smile:

---

### Post by im_ka on 2004-10-28
awright, looking forward to it.
have a nice week-end!

ps: why don't work things in the world the way they do in the open source community?? :(

---

### Post by daniels on 2004-10-28
I have lots of space and bandwidth available also, but that's probably not the best solution.  Most packages should go into the universe repository -- we're slowly growing our maintainence team, but while this is happening, you can also get uploads 'sponsored' into universe or main.

---

### Post by im_ka on 2004-10-29
[QUOTE=daniels]I have lots of space and bandwidth available also, but that's probably not the best solution.  Most packages should go into the universe repository -- we're slowly growing our maintainence team, but while this is happening, you can also get uploads 'sponsored' into universe or main.[/QUOTE]

rodger sir! ;)

---

### Post by nuopus on 2004-10-29
[QUOTE=daniels]I have lots of space and bandwidth available also, but that's probably not the best solution.  Most packages should go into the universe repository -- we're slowly growing our maintainence team, but while this is happening, you can also get uploads 'sponsored' into universe or main.[/QUOTE]
 How do we get packages into universe though?

---

### Post by jdodson on 2004-10-29
[QUOTE=im_ka]awright, looking forward to it.
have a nice week-end!

ps: why don't work things in the world the way they do in the open source community?? :([/QUOTE]

one reason could be because we realize our common focus and brotherhood in gnu/linux and that it betters humanity.  most people(i fear) focus more on differences that commonalities.  focusing on differences draws a line between people that would otherwise be united.

---


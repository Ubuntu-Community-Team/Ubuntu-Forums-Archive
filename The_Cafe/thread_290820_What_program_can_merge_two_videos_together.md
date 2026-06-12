---
title: "What program can merge two videos together?"
date: 2006-11-01
forum: The Cafe
---

### Post by user1397 on 2006-11-01
i've got a 4.2 GB mpeg made by tovid, and the last like 10 minutes of the movie were created in a seperate file thats only 500 MB.  couldn't i merge these two so i can burn one movie to a dvd?

---

### Post by kkinder on 2006-11-01
There's a video editor called kino that should do it. It's packaged, although it might be in universe/multiverse.

---

### Post by user1397 on 2006-11-01
> **kkinder said:**
> There's a video editor called kino that should do it. It's packaged, although it might be in universe/multiverse.ah, ok, thanks.

edit: kino doesn't work, it won't import my mpeg video, it says it has to be DV format (i dont know what that is)

edit:  hmm, GOPchop looks promising...let's see...

---

### Post by kuja on 2006-11-01
I'm more than sure mencoder can do it, but I'm not sure what the command to do so would be.

---

### Post by user1397 on 2006-11-01
> **kuja said:**
> I'm more than sure mencoder can do it, but I'm not sure what the command to do so would be.didn't think about that.  i'll man it, and see what i can do.  thanks for your suggestion.

btw, GOPchop is quite mysterious to me... i think it's only to edit one file.

---

### Post by user1397 on 2006-11-01
wow the mplayer/mecoder man page is 7494 lines long...kinda hard to find ur way around. (so no i wasnt able to find mecoder commands specific to my situation, but i think i'll take a second look.

---

### Post by user1397 on 2006-11-01
is there a way to gedit man pages?

---

### Post by %hMa@?b&lt;C on 2006-11-01
cinelerra should do the job.

---

### Post by Tyl3r on 2006-11-01
Avidemux is cool and easy for things like this.

---

### Post by user1397 on 2006-11-01
> **jeffc313 said:**
> cinelerra should do the job.are you talking about 'xmovie'?  because that is the only program listed if you search for cinelerra (and its just a movie player)

---

### Post by user1397 on 2006-11-01
> **Tyl3r said:**
> Avidemux is cool and easy for things like this.ah, i haven't thought about it.  ](*,) let's see if it works.

---

### Post by ice60 on 2006-11-01
i always just cat everything together, it works a lot of the time. maybe the headers will break though with mpeg ???

make copies first!!!

cat file1.mpeg file2.mpeg >file.mpeg

---

### Post by user1397 on 2006-11-01
wow, impressed by avidemux.  in avidemux, i just opened the first movie file, which was in the same folder as the second movie file, and avidemux instantly recognized both, and made them into one continous film.  just wow.

---

### Post by %hMa@?b&lt;C on 2006-11-01
> **erik1397 said:**
> are you talking about 'xmovie'?  because that is the only program listed if you search for cinelerra (and its just a movie player)

cinelerra isnt in the repos
[http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3)
you may/may not find a deb. most likely will have to alien an rpm

---

### Post by user1397 on 2006-11-01
> **ice60 said:**
> i always just cat everything together, it works a lot of the time. maybe the headers will break though with mpeg ???

make copies first!!!

cat file1.mpeg file2.mpeg >file.mpegdamn, this worked too!  i played the new movie in gxine, and it didn't even skip at the part where the two movie files joined!

this is definitely a lot easier than avidemux or anything else as a matter of fact.  thanks!

---

### Post by BlueStreak on 2006-11-01
that is awesome!  never crossed my mind to use cat for video files.  Great!

---

### Post by ice60 on 2006-11-02
i think it's always a good idea to ask a question like this -

what's the command to... 

lol

---

### Post by rvoro on 2009-10-18
You can use the following mencoder command-line command:

```
mencoder -oac copy -ovc copy VIDEO1.avi VIDEO2.avi -o VIDEO.avi
```

Just replace VIDEO1.avi and VIDEO2.avi with your two files, and replace VIDEO.avi with whatever you want your merged video to be titled.

Reference: [HTML]http://ubuntuforums.org/showthread.php?t=762471[/HTML]

---

### Post by cariboo on 2009-10-18
@rvoro

You are answering a three year old thread that has been answered several times over.. We call this thread necromancy.

This thread is closed.

---


---
title: "phaseal player - music player w/ effects processing &amp; automation"
date: 2016-12-23
forum: The Cafe
---

### Post by zelux2 on 2016-12-23
**Hello folks :smile:**

[COLOR=#000000][INDENT]

So I wrote this music player, I'm gonna call it "phaseal player". It's a music player centered
around audio effects processing, a little similar to audacious and DAWs in general, but it operates
as a keyboard-driven music player that can be run in the terminal or eventually, hopefully in its
own separate window after some more development has been put into it. It processes a handful
of interesting effects at run-time and can be scheduled to automate nearly anything that can
be done with user input on its own. The effects are stacked on top of each other in a specific
order to hear all non-conflicting effects processed simultaneously. Also it has a pipelined methodology 
that enables settings to be automated in a relative manner. For example, you could set individual 
amplify settings to multiple songs in a play list but play each song at 50% of its scheduled setting when
you move the amplify parameter to 50% on a normal track.


you can dowload it here [zerosweet.org/pplayer/download ]("http://zerosweet.org/pplayer/download")
I would certainly like to make a package for this distribution, I just haven't had time to yet.


These commands that are automated by the music player are saved via plain-text playlist files that
are lists of the tracks by media file path with a command chart beneath each filename
(if it has one) that is listed in order of song times, which can be in seconds (X:XX), or beat
relative formats (1+1/4 etc). Speaking of which song tempos can also be saved as sort of annotations
that go with the playlists. The tempos can be figured out during run-time by tapping the space bar to the
beat. In turn, a handful of effects within the program can operate to the beat of the song. For example,
you could set the song tempo, and then set the echo to 1 beat, 1/2 a beat, 1+1/2 beats etc...


I'll try to record some more demo videos and hopefully write some kind of manuals soon,
in the mean-time, you can press f1 at any view in the program to see a list of commands that are 
possible, also there are 2 demo videos I recorded even though they are admittedly lacking & I should probably
do some better ones.


If you might be interested please be obliged to try the program out, I've been using it myself and
enjoy it quite a bit, at least when I'm not busy working on it. When I was a teenager I used to enjoy listening
to music backwards (still do of course) so I'd often save little edits of my favorite songs after reversing
them w/ audacity. All that can get tiresome of course, even with a nice fast program like sox (which I do love),
and I find myself often just wanting to hear what a new cool song sounds like in reverse but the effort to drag
it into some audio program and save a copy somewhere often discourages me from doing so. So having this program
can address those kinds of issues if you are a bit like me.


This is my beta-release of the program, so if you use it and run into any kinds of bugs, or the program crashes or anything like
that, I would be super grateful to anyone who files an issue on the bitbucket issue tracker I have set up.
you can get to that from [bitbucket.org/zelux/phaseal-player/issues ]("http://bitbucket.org/zelux/phaseal-player/issues")or if I mistyped that I also put a link to that page
on [zerosweet.org/pplayer/issues ]("http://zerosweet.org/pplayer/issues")I hope this is a good sub-forum to post this thread, I scanned the list and this seemed like 
the most appropriate choice.


ok, thanks for reading, have a wonderful day !
- cheers

[IMG]http://zerosweet.org/img/scrot1-small.png[/IMG][/INDENT]
[/COLOR]

---


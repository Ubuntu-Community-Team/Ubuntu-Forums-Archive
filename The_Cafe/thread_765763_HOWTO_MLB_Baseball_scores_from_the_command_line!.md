---
title: "HOWTO: MLB Baseball scores from the command line!"
date: 2008-04-24
forum: The Cafe
---

### Post by AaronMT on 2008-04-24
I often want to check the baseball score without opening a browser. (That's right, it's too much work. And sometimes not appropriate at work, considering how much I check it.) So I wrote this very simple command line to fetch and parse the ESPN MLB scoreboard page.

Here's some sample output 

```
AMERICAN LEAGUE - GAME 1
   Top 5th
   Toronto (10-12, 5-5 away)
   Tampa Bay (10-11, 6-7 home)
   1 2 3 4 5 6 7 8 9
   0 0 2 0 0
   0 0 1 1
   R H E
   2 5 0
   2 3 0
   GameCast | Box Score | RealTime [in.gif] | Watch
   Balls: Strikes: Outs:
   Pitching: Sonnanstine (TAM) 4.1 IP, 2 ER, 3 K
   Batting: Inglett (TOR) 0-0
   Pitch 4: ball 3

```

Here's the command line

:KS Note you will need Lynx (a non graphical browser) 
```
sudo apt-get install lynx
```:KS

```
lynx -nonumbers -dump http://scores.espn.go.com/mlb/scoreboard | egrep -i -A12 -B2 Toronto
```

Replace Toronto with your city.

:KS :KS

---

### Post by nerdman978 on 2008-04-24
that's amazing nice work! :guitar:

---

### Post by cardinals_fan on 2008-04-24
Thanks for this - I just had to put quotes around "St. Louis" ;)

---

### Post by elmer_42 on 2008-04-24
That is awesome. I need to add that to Conky. Thanks, man!

EDIT: *Hmm... how to auto-update it every few minutes... hmm...*

---

### Post by SuperSon!c on 2008-04-24
can you do one for the nhl?  :/

---

### Post by AaronMT on 2008-04-24
> **SuperSon!c said:**
> can you do one for the nhl?  :/

Replace "MLB" with "NHL". You'll have to do a little playing around to get the output you like in the egrep parameter.

```
lynx -nonumbers -dump http://scores.espn.go.com/nhl/scoreboard | egrep -i -A12 -B2 Colorado
```

You'll have to fix the output, but it should be easy,

---

### Post by SuperSon!c on 2008-04-25
you my friend, rock!  thanks!  atm i'm having problems getting anything from the repos, but will continue trying.

---

### Post by AaronMT on 2008-04-25
Glad it worked out for ya :)

---

### Post by elmer_42 on 2008-04-25
Hello everybody! A very helpful guy in [this]("http://ubuntuforums.org/showthread.php?t=765841") thread helped me. The code I use for my MLB section is this (from .conkyrc):
```
${color 457ccc}MLB ${hr 2}$color
${color 457ccc}Boston Red Sox $color
${texeci 7200 lynx -nonumbers -dump http://scores.espn.go.com/mlb/scoreboard | egrep -i -A12 -B2 Boston}
${color 457ccc}Florida Marlins $color
${texeci 7200 lynx -nonumbers -dump http://scores.espn.go.com/mlb/scoreboard | egrep -i -A12 -B2 Florida}
```
and here is what it looks like:
[img]http://arch.kimag.es/share/32546473.png[/img]

---

### Post by agim on 2008-04-26
Great program! Works like a charm, except I cannot get it to work for the Yankees. I think the two word city is throwing it off. If anyone can help it would be much appreciated.

---

### Post by Brunellus on 2008-04-26
holy cow this is GREAT.

Try escaping a two word city with a backslash

New\ York

(Look:  Ubuntu is so helpful we even help Yankees fans!  :) )

---

### Post by dvdgorila on 2008-04-26
Actually you can use quotes like so 
```
lynx -nonumbers -dump [http://scores.espn.go.com/mlb/scoreboard](http://scores.espn.go.com/mlb/scoreboard) | egrep -i -A12 -B2 "NY Yankees" 
```

I have it set up that way. GO YANK! :)

---

### Post by cardinals_fan on 2008-04-26
I'm really enjoying this in my Conky - can you guess which team I check?

---

### Post by Kingsley on 2008-04-26
> **cardinals_fan said:**
> I'm really enjoying this in my Conky - can you guess which team I check?

The Chicago Cubs? I'm just guessing here.

---

### Post by cardinals_fan on 2008-04-26
> **Kingsley said:**
> The Chicago Cubs? I'm just guessing here.
I will smite your evil soul! ;)

I realized that for actual game viewing, Conky isn't much use - unless I have it update obscenely often.  So, I have used the following .conkyrc segment to tell me who's playing, and if I'm interested, I can check the main action manually.

```
${offset 12}${voffset 80}${color c90006}${font HeldustryFTVBasic Demi:size=10}St. Louis Cardinals
${voffset 10}${color 9d9d9d}${font HeldustryFTVBasic Demi:size=10}${texeci 3600 scores | grep -B 1 "home"}
```
Where 'scores' is an alias for: ```
lynx -nonumbers -dump http://scores.espn.go.com/mlb/scoreboard | egrep -i -A12 -B2 "St. Louis"
```

Screenshot attached:

---

### Post by drworm01 on 2008-05-01
Does anyone have a link to a teams-to-code translator or key? I'm trying to get the Houston Astros to work, but no luck. "Texas" pulls up the Rangers and "Houston" grabs nothing. This is really neat code though. Thanks for posting it.

---

### Post by cardinals_fan on 2008-05-01
> **drworm01 said:**
> Does anyone have a link to a teams-to-code translator or key? I'm trying to get the Houston Astros to work, but no luck. "Texas" pulls up the Rangers and "Houston" grabs nothing. This is really neat code though. Thanks for posting it.
Everything has stopped working for the moment - I'll mess about with the code to see if I can fix it.

Never mind, my wireless had a hiccup ;)

---

### Post by jetsam on 2008-05-01
Houston's just not playing today.  "Houston" works for yesterday if you put the date code in the URL:
```
lynx -nonumbers -dump http://scores.espn.go.com/mlb/scoreboard?date=20080430 | egrep -i -A12 -B2 'Houston'

```

I figured this out by just looking at the actual website in Firefox:
[http://scores.espn.go.com/mlb/scoreboard]("http://scores.espn.go.com/mlb/scoreboard")

That's no fun, though.  ;-)

---

### Post by drworm01 on 2008-05-01
> **jetsam said:**
> Houston's just not playing today.  "Houston" works for yesterday if you put the date code in the URL:
```
lynx -nonumbers -dump http://scores.espn.go.com/mlb/scoreboard?date=20080430 | egrep -i -A12 -B2 'Houston'

```

I figured this out by just looking at the actual website in Firefox:
[http://scores.espn.go.com/mlb/scoreboard]("http://scores.espn.go.com/mlb/scoreboard")

That's no fun, though.  ;-)

Thanks. I thought that might be the case, but I wasn't sure if the code grabbed the current game or just the most recent. That's good to know.

---

### Post by waldorsockbat on 2008-05-03
Let me start by saying thanks for the great work on this,It's nice to see some sports fans here.I need a little help with this. In the screen shot you can see that the score stops at the sixth inning for the home team,everything is fine until the 8th inning and it reverts to this for the home teams only.I have googled for the code help but can't find anything to fix it.

---

### Post by AaronMT on 2008-05-04
Yeah like I said, it's just a matter of playing around with the right parsed output, the logic remains the same (ie, Use Lynx to fetch the content).

---

### Post by waldorsockbat on 2008-05-04
I have tried playing around with parsed output but I cant get it to work correctly.It would be nice to get the output of the commnad in the terminal to be the same as in conky,I am trying to get the output in a second conky but without much luck.As you can tell I am still somewhat new to conky code.

---

### Post by AaronMT on 2008-05-08
bump

---

### Post by HangukMiguk on 2008-05-08
Mine is showing a bunch of highlight links underneath in conky (Box score, play-by-play, etc.)

---

### Post by jetsam on 2009-04-06
Hmm.  'Tis the season, and this doesn't work very well any more because ESPN changed their page layout.  

Anyone have any ideas on how to fix?

---

### Post by gschroder on 2009-04-14
Okay... hopefully I can provide a service, in exchange for a little help.  :)  I can get around the issue with the formatting of the ESPN site.  But I need some Conky support.

[COLOR="DarkGreen"]*I just got my first Ubuntu machine a week ago (a Dell Mini 9) and installed Conky yesterday... and really have no idea how to set this up in my config file to get it to update properly.  So if someone would be willing to share a snippet of their config file in exchange, I would greatly appreciate it!*[/COLOR]

Instead of using the ESPN feed, I use 4Info (m.4info.com).  It is a WAP site designed for older cell phones -- and the formatting of the pages have not changed in years.  The pages are super bare bones and offers sports, weather and other info.

When I do a search on a team name (like the Tribe) and then click on the link for the team name, I get a URL like this:  [http://m.4info.com/search?searchQuery=Cleveland+Indians](http://m.4info.com/search?searchQuery=Cleveland+Indians)

I then format the lynx command like this:
```
lynx -nonumbers -nolist -dump [http://m.4info.com/search?searchQuery=Cleveland+Indians](http://m.4info.com/search?searchQuery=Cleveland+Indians) | egrep -i -B2 -A4 "Status"
```


...which gets me this output:
```
Cleveland Indians  (1-6)   (R) 2    (H) 10    (E) 0
Kansas City Royals (4-3)   (R) 4    (H) 5    (E) 0
Status:  Final
Date:  4/13
Winning Pitcher: Zack Greinke  (2-0)
Losing Pitcher: Fausto Carmona  (0-2)
Saving Pitcher: Joakim Soria  (4 saves)
```

---

### Post by gschroder on 2009-04-14
Aha.  I found this post that had the answer: [http://ubuntuforums.org/showthread.php?t=765841](http://ubuntuforums.org/showthread.php?t=765841)

Now I can follow every agonizing step in the Indians' terrible 1-6 start to the 2009 season right on my desktop. :neutral:

---

### Post by jetsam on 2010-05-02
Much belated thanks to gschroder.  I somehow missed the solution even though I asked for it last season.  

I'll be using this without doubt this season.  

...

Sometimes all I really wanna know, though, is [Who's on First?!]("http://www.youtube.com/watch?v=Watf8_Rf58s")

---

### Post by halflifez on 2010-05-08
I"m just configuring my conky script using Lynx to fetch the content.
I've managed to fetch the correct data, but I only want the "EAST" division to show and not the central. Below is the input and output.

Thanks in advance!!!

nitro@nitro-laptop:~$ lynx -nonumbers -dump [http://scores.espn.go.com/mlb/standings](http://scores.espn.go.com/mlb/standings) | egrep -A12 "American League"   American League
   EAST           W  L  PCT  GB HOME ROAD  RS  RA DIFF   STRK L10
   Tampa Bay     22  8 .733   -  9-6 13-2 174  90  +84 Lost 1 7-3
   NY Yankees    20  8 .714   1 10-2 10-6 161  99  +62  Won 5 8-2
   Toronto       18 13 .581 4.5 7-10 11-3 149 129  +20  Won 6 8-2
   Boston        15 15 .500   7  9-9  6-6 153 160   -7 Lost 1 6-4
   Baltimore      9 21 .300  13  4-8 5-13 106 147  -41  Won 2 5-5
   CENTRAL        W  L  PCT  GB HOME ROAD  RS  RA DIFF   STRK L10
   Minnesota     19 11 .633   -  9-5 10-6 152 115  +37 Lost 2 5-5
   Detroit       17 13 .567   2  9-3 8-10 145 139   +6  Won 1 6-4
   Chicago Sox   12 18 .400   7  8-9  4-9 122 148  -26 Lost 2 4-6
   Kansas City   11 19 .367   8  4-8 7-11 126 165  -39 Lost 3 3-7
   Cleveland     10 18 .357   8  5-8 5-10  99 140  -41 Lost 5 2-8

---

### Post by halflifez on 2010-05-09
Okay I solved it people. All I had to change was the A12 to A6.
A stands for the number of lines. I figured this out and thought it might help anyone out there, thats why I'm posting this.

nitro@nitro-laptop:~$ lynx -nonumbers -dump [http://scores.espn.go.com/mlb/standings](http://scores.espn.go.com/mlb/standings) | egrep -A6 "American League"
   American League
   EAST           W  L  PCT   GB HOME ROAD  RS  RA DIFF   STRK L10
   Tampa Bay     22  8 .733    -  9-6 13-2 174  90  +84 Lost 1 7-3
   NY Yankees    21  8 .724   .5 10-2 11-6 175 102  +73  Won 6 9-1
   Toronto       18 14 .563    5 7-10 11-4 152 136  +16 Lost 1 8-2
   Boston        15 16 .484  7.5 9-10  6-6 156 174  -18 Lost 2 5-5
   Baltimore      9 22 .290 13.5  4-8 5-14 107 153  -46 Lost 1 5-5

---

### Post by halflifez on 2010-05-11
Im trying to write a python script that will have a similar output as above in my conky. Unfortunately there is no output.
NOTE: using the following command, the output is fine but is off centred
TEXT
...
**${texeci 7200 lynx -nonumbers -dump [http://scores.espn.go.com/mlb/standings](http://scores.espn.go.com/mlb/standings) | egrep -A6 "American League"}**



The python script is as follows:

[B]import webbrowser

webbrowser.get('lynx')

lynxcmd = "lynx -nonumbers -dump [http://scores.espn.go.com/mlb/standings](http://scores.espn.go.com/mlb/standings) | egrep -i -A6 American\ League"

data = os.popen(lynxcmd).read()
print data[/B]

any help with this people? It would be really appreciated.

---

### Post by irish_latte on 2010-05-11
This is great!

---

### Post by Bugs318 on 2010-05-27
This is great!  Thanks so much for this!

One more question though that would be really useful... does anybody know a command to see all of the scores on the command line (that could go into conky) or a way to distinguish it with all AL scores?

That would be immensely useful to me, but I am at a loss.

Thanks!

---

### Post by Bugs318 on 2010-06-02
Figured out a way to get all scores for those who are interested:


lynx -nonumbers -dump [http://wap.mlb.com/scores/](http://wap.mlb.com/scores/) | egrep -e vs

---

### Post by smilliken on 2011-05-28
Any idea why my conky does not display the entire data?

```
# --- Window Layout & Options --- #
own_window yes
own_window_colour brown
own_window_transparent yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
use_spacer right
use_xft yes
alignment top_left
gap_x 15
gap_y 5

# --- Colours, Sizes, Fonts & Margins --- #
update_interval 1
maximum_width 500
stippled_borders 3
border_width 9
default_color grey

# --- Text --- #
draw_outline no
draw_borders no
font Crackdown R BRK:size=10:weight=bold
uppercase no
draw_shades yes

TEXT

${color red}MLB ${hr 2}$color
${font freemono:size=10}${color white}${execi 30 lynx -nonumbers -dump http://scores.espn.go.com/mlb/standings | egrep -A12 "American League" }${font}
```

---

### Post by seannyob on 2012-08-08
No idea but mine is the same way, cuts off at Tampa Bay.
It's got to be in teh .conkyrc file, some switch.
Don't know anything about conky but perhaps someone who cares will chime in.
```
# --- Window Layout & Options --- #
own_window yes
own_window_colour brown
own_window_transparent yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
use_xft yes
alignment top_left
gap_x 1300
gap_y 35
# --- Colours, Sizes, Fonts & Margins --- #
update_interval 1
maximum_width 350
stippled_borders 3
border_inner_margin 9
border_width 9
default_color grey

# --- Text --- #
draw_outline no
draw_borders no
font Monospace:size=8:weight=bold
uppercase no
draw_shades no

TEXT
#${texeci 3600 feh --bg-scale "/usr/share/wallpapers/MEPIS11.0-wallpaper.jpg"}
${color lightblue} MLB ${hr 2}$color
${font freemono:size=10}${color white}${execi 30 python ~/.conky/baseball.py}

```

---

### Post by oldos2er on 2012-08-08
Old thread is old. Closed.

---


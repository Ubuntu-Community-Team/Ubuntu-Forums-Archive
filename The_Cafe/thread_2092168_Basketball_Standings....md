---
title: "Basketball Standings..."
date: 2012-12-07
forum: The Cafe
---

### Post by hwttdz on 2012-12-07
```
#!/bin/bash
mkdir -p ~/.nbastandings
cd ~/.nbastandings
wget -q -N http://www.nba.com/standings/team_record_comparison/conferenceNew_Std_Div.html
\grep -A 1000 "genStatTable mainStandings" conferenceNew_Std_Div.html | \grep -B 1000 TIEBREAKER > clean_standings
echo -e "            \tWin\tLoss\tRecord\tGB\tConf\tDiv\tHome\tRoad\tL10\tStreak"
\grep -A 10 -i "${1:-knicks}" clean_standings | perl -0777 -pe 's/^\s+//;s/\n//g;s/>\s+</></g;s/<\/a>/  /;s/<td>/\t/g;s/<[^>]*?>//g'

```

usage: ./get_record
./get_record bulls
./get_record knicks
...

example output:
```
            	Win	Loss	Record	GB	Conf	Div	Home	Road	L10	Streak
Washington  	2	13	0.133	9.0	1-10	1-3	2-6	0-7	2-8	W 1
```

It should play well with cut -f, and if the nba actually put together a reasonable site then the -N in wget would mean we don't kill their servers...

Anyways, I've been wanting standings in my conky.  Defaults to knicks, because I'm a new york guy.  Due to the layout of the page, you name the mascot and it tells you the city...

---

### Post by Erik1984 on 2012-12-07
Nice!

This part confuses me though :P
```
's/^\s+//;s/\n//g;s/>\s+</></g;s/<\/a>/  /;s/<td>/\t/g;s/<[^>]*?>//g'
```

---


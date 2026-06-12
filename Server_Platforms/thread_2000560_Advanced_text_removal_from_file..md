---
title: "Advanced text removal from file."
date: 2012-06-09
forum: Server Platforms
---

### Post by Valpskott on 2012-06-09
Introduction:
I'm about to host a game server (Minecraft) where players will terraform the world. Anyone will be able to connect to the server, including people who just like to be rude by destroying what others have built.

Now, I've installed a plugin where players can basically "Claim" a piece of land (one chunk) which prevents others from causing harm in that chunk. When players Claim a chunk, the server stores the info into a text file.

Now, there will be one area (for beginners) of the world map that I will reset every now and again. The reset of the physical map is all taken care of, but the file that stores who owns what piece of land needs some advanced text editing.



How entries are stored in the file:
```
world_-16_14:
  owner: Server
  allowed: '*:U,*:O'
world_-1_31:
  owner: Valpskott
world_-32_0:
  owner: Valpskott
```


Every claimed chunk takes up 2-3 lines of text in the file depending on if a player has granted other players permission to do stuff in a particular chunk or not.

So, I'd really need help making a script that deletes every entry for coordinates (-1,31) to (-32,0) and the following lines that belongs to each entry.

The entries are not sorted(well, they are in chronological order I guess), and there will be entries outside those coordinates that should not be deleted.

---

### Post by thnewguy on 2012-06-09
From the description of the problem it sounds less like a typical text find/replace operation and more like a small programming exercise. Really it sounds like you're saying "check each line that begins with "world", translate its coordinates into a range and for entries within X1-Y1 to X2-Y2, delete lines until we hit a new world extry.

It can be done, but I'm thinking it would be a pretty ugly shell script. Or a short C program. If you do go ahead with this I'd recommend looking at the "awk" command. It could probably read in each line, check for a value and then either ignore or output the following lines.

---

### Post by Valpskott on 2012-06-10
Thanks for the reply.

I was thinking of having "for"-loops that counts all the relevant cordinates. It's a square of 1024 chunks that should be reset in this fashion.

```
for y in {-31..-1..1}
  do
	for x in {0..31..1}
	  do
	     echo "world_$y""_$x:"
	 done
 done
```

The above code will output something that could be used by GREP I believe.

Now, I'm not too confident in my ability to script, and although a C program could be better, I have no clue where to begin in such an endevour.

Gonna check out the manpage for AWK now and see what it does, thanks for the tip :)

---

### Post by markbl on 2012-06-10
I have been programming in shell script, sed, awk, etc for 25 years. Seriously, python (or perl or ruby) has completely supplanted awk nowadays and sounds like it would be more appropriate here. You don't want to write a C program.

---

### Post by linkageless on 2012-06-10
This is probably achievable in bash, awk, sed etc, but I would use perl - it's absolutely what it was created for.

---

### Post by linkageless on 2012-06-10
I'll see if I can work something in perl up for you... unfortunately RL calls right now but watch this space...

---

### Post by steeldriver on 2012-06-10
you can do a kind of stateful thing in awk I think - by keeping track of the 'current' (lat, lon) and printing only when they are within the given range

```
awk 'BEGIN { FS="[_:]"; lat=-32; lon=32; } {if ($1 == "world") {lat=$2; lon=$3}; if (lat > -1 || lon < 0) print $0;}'
```

---

### Post by Valpskott on 2012-06-10
> **linkageless said:**
> I'll see if I can work something in perl up for you... unfortunately RL calls right now but watch this space...

That would be most helpful since I know nothing about Pearl. And please have some comments in the script so that I can understand what's going on in the script. :)

---

### Post by Valpskott on 2012-06-10
> **steeldriver said:**
> you can do a kind of stateful thing in awk I think - by keeping track of the 'current' (lat, lon) and printing only when they are within the given range

```
awk 'BEGIN { FS="[_:]"; lat=-32; lon=32; } {if ($1 == "world") {lat=$2; lon=$3}; if (lat > -1 || lon < 0) print $0;}'
```



Hmm, wow. Could you break this down for me?:confused:

---

### Post by Valpskott on 2012-06-10
I get the sense that a great deal of time is spent arguing for which language/tools is best for this job.

Now, the file that should be processed will in time grow to a couple of mb in size at most, the computer has 8 cores, 32gb ram and the game-server-software will be offline while processing this file.. so, I'm not as concerned over efficiency as I am concerned over getting a working solution. :)

Other than that, I'm thankful that so many people have shown interest in helping me with this :)

---

### Post by steeldriver on 2012-06-10
> **Valpskott said:**
> Hmm, wow. Could you break this down for me?:confused:

Here's a less-hairy chested version which should be more readable and also tries to make the 'statefulness' more explicit

```

#!/usr/bin/awk -f

BEGIN { 
    # set field separator 
    FS="[_:]"; 

    # initialize (lat, lon) coordinates and state
    lat=32; lon=-32; printstate = 1; 
}
{
    # match world_NN_MM and update (lat, lon)
    if ($1 == "world") {
        lat=$2; lon=$3;
        # print lat, lon; # for debugging

        # use (lat, lon) values to set state
        if (lat < 0 || lon > -1) 
            printstate = 0; 
        else 
            printstate = 1;
    }
    # output lines whenever state is 'true'
    if (printstate == 1) print $0; 
}

```I'm not a regular awker so forgive me if I've done anything dumb and/or ugly - also I probably didn't set the (lat, lon) test condition right, you will need to check and adjust that if necessary

---

### Post by linkageless on 2012-06-10
That awk solution looks like a fine one (although I've not looked at it carefully or tested).  Mostly for my own satisfaction, I've finished this perl one that I started before being dragged away. As performance isn't an issue the only likely functional difference is the way you would use them. (As I recall you could expect perl to easily outperform awk, but then my code is far from optimised. YMMV :)

```
#!/usr/bin/perl -w
# for filtering lines matching a pre-defined coordinate spec

# the criteria are coordinates (-1,31) to (-32,0)
my $low_x=-32;
my $high_x=-1;
my $low_y=0;
my $high_y=31;

# initialise discard flag
my $dropme = 0;

# while there are lines to read on stdin (or as an argument), keep reading them
while (<>) {
  # if this is a 'world' line, reset our expectations
  if ($_ =~ /^world_(\-?\d+)_(\-?\d+):/) {
    $dropme = 0;
    # check if this is one of the ones we don't want
    if (($1 >= $low_x) && ($1 <= $high_x) && ($2 >= $low_y) && ($2 <= $high_y)) {
      # discard lines from here
      $dropme = 1;
      # show discarded line on stderr
      warn "discarded: $_";
    } else {
      # we want this line, print to stdout
      print $_;
    }
  } else {
    # this isn't a 'world' line, so only discard if $dropme is set
    if ($dropme > 0) {
      warn "discarded: $_";
    } else {
      print $_;
    }
  }
}

```

I would probably use this like so:
```

date >> logfile && ./script.pl infile > outfile 2>> logfile

```
('logfile' will have date stamps and the stderr output from the script showing what has been discarded.)

I've not tested this thoroughly, and I'm only going on the sample data you've shown but perhaps this will help you along the way. 
[http://www.perlmonks.org/](http://www.perlmonks.org/) will doubtlessly be most useful for a more elegant solution.

Also, I've found there's a few minecraft associated perl projects. This may be useful for example: [https://github.com/kevinbosak/Minecraft-Perl](https://github.com/kevinbosak/Minecraft-Perl)

Hope that helps.

---

### Post by Valpskott on 2012-06-10
Thanks to both of you for taking time and energy to help me with this! I tried out the script provided by linkageless since it was easier for me to see how I should implement/execute it.

I've tested it a few times and it looks like it works. All chunks in the area are shown as unclaimed after running the script! :)

You guys are awesome, cause this was kind of a deal-breaker for how I wanted my server to be.

---

### Post by linkageless on 2012-06-11
It's a pleasure to be of assistance! Don't let me put you off trying awk though, I use it almost on a daily basis on the command line.

---


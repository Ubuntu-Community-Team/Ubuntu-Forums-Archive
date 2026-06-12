---
title: "[SOLVED] Help us count down to 500,000 members!"
date: 2008-02-09
forum: The Cafe
---

### Post by jdong on 2008-02-09
We are on the verge of breaking the 500,000 members mark. It'd be great to have a screenshot of this momentous landmark in UbuntuForums history, so everyone keep your eyes open on the homepage!

(And if that's some special field only I can see, feel free to hit me with blunt objects)

---

### Post by FuturePilot on 2008-02-09
493 to go :guitar:

---

### Post by LaRoza on 2008-02-09
It should be there in 12 - 15 hours, based on the past statistics.

---

### Post by LookTJ on 2008-02-10
Congratulations to our 500,000th [member]("http://ubuntuforums.org/member.php?u=501180") of the Ubuntu Forums: djablo

---

### Post by hhhhhx on 2008-02-10
someone should register the name '500'000th' right when were at 499.999 :)

---

### Post by Presto123 on 2008-02-10
> **xhhux said:**
> someone should register the name '500'000th' right when were at 499.999 :)

LOL I would almost stay up just long enough to keep refreshing to register that one!

---

### Post by BigSilly on 2008-02-10
500,000!!

But where are we going to put them all?

:shock:

---

### Post by hhhhhx on 2008-02-10
only 396 left, that means it went from 493 to 396 in 3hrs!! :)

---

### Post by LaRoza on 2008-02-10
> **xhhux said:**
> only 396 left, that means it went from 493 to 396 in 3hrs!! :)

Moving slow today it is.

---

### Post by hhhhhx on 2008-02-10
> **LaRoza said:**
> Moving slow today it is.
ya, but its like 1:50 am, also i notice your avatar is changed back.

---

### Post by LaRoza on 2008-02-10
> **xhhux said:**
> ya, but its like 1:50 am, also i notice your avatar is changed back.

Yeah, I changed it a couple days ago.

0519 here

---

### Post by Vadi on 2008-02-10
The forums were down..

but "Members: 499,929" now

---

### Post by jpeddicord on 2008-02-10
A few hours left!

---

### Post by corney91 on 2008-02-10
499,931 now

---

### Post by popch on 2008-02-10
You are all counting up. The thread's title says to count down.

---

### Post by corney91 on 2008-02-10
> **popch said:**
> You are all counting up. The thread's title says to count down.
Sorry, 63 then!:)

---

### Post by benerivo on 2008-02-10
Given the current time, it's probably going to be someone in western europe or the americas. Does the 500,000th person win 1 minutes worth of free shopping in the ubuntu store?! 60.

---

### Post by corney91 on 2008-02-10
Wow. 54. There's probably a surge because of the maintenance...

---

### Post by Danni on 2008-02-10
50 to go!

---

### Post by meho_r on 2008-02-10
49:)

---

### Post by jdong on 2008-02-10
> 16:13 <+dongbotu> New Member 499949 is sonhodemiurgo, 51 more to go
16:16 <+dongbotu> New Member 499950 is rommie7, 50 more to go
16:17 <+dongbotu> New Member 499951 is RumorsOfWar, 49 more to go


If anyone wants to join in #ubuntuforums on irc.freenode.org, I have set up a bot that's counting us down to 500,000 :)

---

### Post by forestpixie on 2008-02-10
what's the 500000th member gonna get - some free software :D

---

### Post by FuturePilot on 2008-02-10
A free copy of Ubuntu :D

---

### Post by Superkoop on 2008-02-10
> **FuturePilot said:**
> A free copy of Ubuntu :D


Lucky! :O

---

### Post by sloggerkhan on 2008-02-10
41 to go. I thought it would take a bit longer to reach 500000.

---

### Post by Midwest-Linux on 2008-02-10
1/2 million members? Cool, is that a record? 
What is the forum with the most members? 
Are we going into the Guinness World Book of Records?

 I wonder how many of the half million use Linux, and how many of them use more than one Linux distro on their computer. Ballmer must be getting nervous...lol 

Congrats to Ubuntu forums!

---

### Post by jdong on 2008-02-10
Ok, just in case anyone else wants to do voodoo fortune telling like:

> 
16:43 <+dongbotu> New Member 499966 is paulbarnes, 34 more to go
16:43 <+dongbotu> Judging from the past 20 members in 2174 seconds (108 seconds/member),  1h1m35s left to go


But hopefully more statistically correct than linear extrapolation.... I have made logs available at [http://jdong.mit.edu/~jdong/forums-members.txt](http://jdong.mit.edu/~jdong/forums-members.txt).

Example parsing code at end. **Please do not wget or otherwise scrape the forum** -- it increases load on the servers.



```

require "time"
class TimeInterval
  @@unit_map={:s => 1, :m => 60, :h => 3600,
              :d => 86400, :w => 604800}
 attr_accessor :val
  def initialize(i)
    @val=i
  end
  def to_i
    @val
  end
  def to_s
    val=@val
    s=String.new
    if val < 0
      s << "-"
      val *= -1
    end
    tokens=Hash.new
    @@unit_map.sort_by{|k,v| -v}.each do  |unit, n|
      tokens[unit]=(val/n).to_i
      val=val-tokens[unit]*n
      if tokens[unit] != 0
        s << "#{tokens[unit]}#{unit}"
      end
    end
    s
  end
  def self.from_s(s)
    time_tokens=s.scan(/([\d]+)([wdhms])/)
    # Tokens are [ ["1","d"], ["3","m"] ] and so on
    # Now, let's convert these to seconds
    secs=0
    time_tokens.each do |quantity, unit|
       next unless quantity and unit
       secs+= quantity.to_i*@@unit_map[unit.to_sym]
    end
    if s =~ /^-/
      secs *= -1
    end
    return TimeInterval.new(secs)
  end
end

timediffs=Array.new
epoch=nil
members=0
File.open("/tmp/members","r") do |f|
   f.each_line do |l|
      next if l.empty?
      t=Time.parse(l.scan(/(^.*) New/).flatten[0])
      unless epoch
         epoch=t
      else
         timediffs << (t-epoch).abs
         epoch=t
      end
      members=l.scan(/Member ([\d]+)/).flatten[0].to_i
   end
end
def sum(list)
   s=0
   list.each {|i| s+=i.to_i}
   s
end
timediffs=timediffs.slice(timediffs.length-20,timediffs.length)
puts "Judging from the past #{timediffs.length} members in #{sum(timediffs)} seconds (#{(sum(timediffs).to_f/timediffs.length).to_i} seconds/member), #{TimeInterval.new((500000-members)*sum(timediffs).to_f/timediffs.length)} left to go"

```

---

### Post by Mazza558 on 2008-02-10
> **Midwest-Linux said:**
> 1/2 million members? Cool, is that a record? 
What is the forum with the most members? 
Are we going into the Guinness World Book of Records?


IIRC, Gaia Online (random online Japanese MMO) has about 4 million members.

---

### Post by AsoSako on 2008-02-10
499,976

---

### Post by Midwest-Linux on 2008-02-10
> **Mazza558 said:**
> IIRC, Gaia Online (random online Japanese MMO) has about 4 million members.


 We must be the most popular Linux forum out there.

---

### Post by hhhhhx on 2008-02-10
499,986,  why are there 2 threads about this?

---

### Post by jdong on 2008-02-10
> **xhhux said:**
> 499,986,  why are there 2 threads about this?
Well obviously I'm more important so this thread is the real one. (kidding :D)

---

### Post by Dr Small on 2008-02-10
13 left :)

---

### Post by hhhhhx on 2008-02-10
9 leaft!!, so close, yet so far

---

### Post by Dr Small on 2008-02-10
6 left!!!

---

### Post by p_quarles on 2008-02-10
Got an early screenshot.

---

### Post by hhhhhx on 2008-02-10
6 left // how come if you go to the profile of the 500000th, its already taken

[http://ohioloco.ubuntuforums.org/member.php?u=500000](http://ohioloco.ubuntuforums.org/member.php?u=500000)


EDIT ; 5 members left!
EDIT : 3 members
EDIT 2 mem

---

### Post by xeth_delta on 2008-02-10
5 to go!

---

### Post by mali2297 on 2008-02-10
4,3,..

---

### Post by benerivo on 2008-02-10
[QUOTE=xhhux;4306288]6 left // how come if you go to the profile of the 500000th, its already taken

[http://ohioloco.ubuntuforums.org/member.php?u=500000](http://ohioloco.ubuntuforums.org/member.php?u=500000)

Don't know, but 500,550 has also been taken.

---

### Post by matthew on 2008-02-10
> **xhhux said:**
> 6 left // how come if you go to the profile of the 500000th, its already taken

[http://ohioloco.ubuntuforums.org/member.php?u=500000](http://ohioloco.ubuntuforums.org/member.php?u=500000)


EDIT ; 5 members left!
EDIT : 3 members
EDIT 2 memEarly on in the forum's history we used to allow user accounts to be deleted...then we later discovered it can do odd things in the database, so we don't allow it anymore. Anyway, that's why the discrepancy exists.

---

### Post by eye208 on 2008-02-10
499,998...

---

### Post by benerivo on 2008-02-10
> **xhhux said:**
> 6 left // how come if you go to the profile of the 500000th, its already taken

[http://ohioloco.ubuntuforums.org/member.php?u=500000](http://ohioloco.ubuntuforums.org/member.php?u=500000)


EDIT ; 5 members left!
EDIT : 3 members[/QUOTE]

Don't know, but 500,550 has also been taken.

---

### Post by AsoSako on 2008-02-10
Threads: 674,839,                 Posts: 4,294,458,                 Members: 500,000             
             Welcome to our newest member, [djablo]("http://ubuntuforums.org/member.php?u=501180")
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=59310&stc=1&d=1202682357[/IMG]

---

### Post by xeth_delta on 2008-02-10
Happy 500000th user, Ubuntu forums! ;)

---

### Post by hhhhhx on 2008-02-10
499999 :
[http://stashbox.org/80809/Screenshot-1.png](http://stashbox.org/80809/Screenshot-1.png)

500000 : 
[http://stashbox.org/80812/Screenshot-2.png](http://stashbox.org/80812/Screenshot-2.png)

500000 user :
[http://ohioloco.ubuntuforums.org/member.php?u=501180](http://ohioloco.ubuntuforums.org/member.php?u=501180)

---

### Post by popch on 2008-02-10
Well, it's done. Well done.

Mark the thread as 'solved', then, please.

---

### Post by jpeddicord on 2008-02-10
[size=7]500,000![/size]

---

### Post by FuturePilot on 2008-02-10
Whoohooo!!!!11!! :guitar:

---

### Post by -grubby on 2008-02-10
just missed the screenshot. My luck :(

---

### Post by matthew on 2008-02-10
Woohoo! Thanks for the screenshots. My attempt captured 500,001...

---

### Post by corney91 on 2008-02-10
> **matthew said:**
> Woohoo! Thanks for the screenshots. My attempt captured 500,001...
Ditto:(
Ah well, life goes on and ubuntuforums continue to prosper....

---

### Post by corney91 on 2008-02-10
500,073.

...we not carrying on to a million??:)

---

### Post by JT9161 on 2008-02-10
[http://www.digg.com/linux_unix/Ubuntu_Forums_reaches_500_000_users](http://www.digg.com/linux_unix/Ubuntu_Forums_reaches_500_000_users)

---

### Post by josh.tessin on 2008-02-10
Wooohoo! I can't wait until the 5,000,000 user.

---

### Post by andrewabc on 2008-02-11
> **matthew said:**
> Early on in the forum's history we used to allow user accounts to be deleted...then we later discovered it can do odd things in the database, so we don't allow it anymore. Anyway, that's why the discrepancy exists.

So someone could have created an account 4 years ago and made no posts, and still be in the database? seems like a waste of space to me. I thought pruning users with no posts was normal for forums

---

### Post by jdong on 2008-02-11
> **andrewabc said:**
> So someone could have created an account 4 years ago and made no posts, and still be in the database? seems like a waste of space to me. I thought pruning users with no posts was normal for forums


Well as always said, storage is cheap and the 5KB or whatever needed to store the e-mail address and post count of a user is not as much of an issue as the namespace cluttering.

Sooner or later, a purge/prune would not be a bad idea to free up some usernames for everyone's benefit.

---

### Post by aimran on 2008-02-11
Not doing anything for the 500kth member? Like custom user title "500,000th" member?

---

### Post by jdong on 2008-02-11
I don't think the 500,000th user needs any more harassment than what has already been propagated ;-)

I wouldn't be surprised if he/she's sifting through 1000 private messages and has a full e-mail inbox by now :D

---


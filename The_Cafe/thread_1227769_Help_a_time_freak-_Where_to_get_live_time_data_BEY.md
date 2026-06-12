---
title: "Help a time freak- Where to get live time data BEYOND seconds?"
date: 2009-07-31
forum: The Cafe
---

### Post by BastardNamban on 2009-07-31
I'm a watch & clock afficianado, and I like testing the timing errors on my timepieces. Thing is, I'm meticulous. I know of NTIS and the Greenwich Observatory sites, obviously, and I have FoxClocks in Firefox, but everything only shows live time data to the second. I want something more accurate! Cesium clocks and whatnot.

I've been to the actual Greenwich observatory in London, so I know they have ultra-accurate clocks there, and several live feeds of time on LED marquis of time to something like the current microsecond. But I can't seem to find any website displaying this info, or even attempting to (I'd imagine it may have to do with the load sync lag or something).

Does anyone know of any site that shows time data live for anything beyond seconds? Even tenths of a second would be a huge improvement in timing my watch for errors.

Any help?

And if you're thinking, "past seconds? Your hand can't act fast enough on the pusher to make up for it anyway!"- I'm thinking of syncronizing some sort of high-speed servo crown pushing rig to set my watches with a site using some sort of script or something.

---

### Post by Chronon on 2009-07-31
I would think that the latency involved in transmitting any signals over the internet would make this an impossible task.  You need some kind of direct, low latency signal straight from one of these referenced clocks.  Synching over the internet can prevent cumulative errors, but can't eliminate the offset beyond a certain level.

---

### Post by jomiolto on 2009-07-31
On the top of my head, the only thing that springs to mind is [radio clocks]("http://en.wikipedia.org/wiki/Radio_clock").

---

### Post by wojox on 2009-07-31
[http://www.usno.navy.mil/USNO/time](http://www.usno.navy.mil/USNO/time)

---

### Post by HappinessNow on 2009-07-31
> Time slows under intense gravity and extreme velocity. You get          near the speed of light, and time just about stops. And you don't have          to take our word for it. Albert Einstein, icon of modern physics, figured          this one up, and nobody's done anything but [prove him right]("http://whyfiles.org/052einstein/").

We always assumed that time, like tide, waits for nobody -- then we          learned that on Dec. 31, 1998, scientists spliced in an extra second because          the Earth was running slower than the atomic clocks. [http://whyfiles.org/078time/](http://whyfiles.org/078time/)

Here is one in nanoseconds:

> A [Time::Clock]("http://search.cpan.org/%7Ejsiracusa/Time-Clock-0.12/lib/Time/Clock.pm") object is a twenty-four hour clock with nanosecond precision and wrap-around. It is a clock only; it has absolutely no concept of dates. Vagaries of date/time such as leap seconds and daylight savings time are unsupported.
  When a [Time::Clock]("http://search.cpan.org/%7Ejsiracusa/Time-Clock-0.12/lib/Time/Clock.pm") object hits 23:59:59.999999999 and at least one more nanosecond is added, it will wrap around to 00:00:00.000000000. This works in reverse when time is subtracted.
  [Time::Clock]("http://search.cpan.org/%7Ejsiracusa/Time-Clock-0.12/lib/Time/Clock.pm") objects automatically stringify to a user-definable format.
[http://search.cpan.org/~jsiracusa/Time-Clock-0.12/lib/Time/Clock.pm]("http://search.cpan.org/%7Ejsiracusa/Time-Clock-0.12/lib/Time/Clock.pm")

```
  $t = Time::Clock->new(hour => 12, minute => 34, second => 56);
  print $t->as_string; # 12:34:56

  $t->parse('8pm');
  print "$t"; # 20:00:00

  print $t->format('%I:%M %p'); # 08:00 PM

  $t->add(minutes => 15, nanoseconds => 123000000);
  print $t->as_string; # 20:15:00.123

  $t->subtract(hours => 30);
  print $t->as_string; # 14:15:00.123

```[http://search.cpan.org/~jsiracusa/Time-Clock-0.12/lib/Time/Clock.pm]("http://search.cpan.org/%7Ejsiracusa/Time-Clock-0.12/lib/Time/Clock.pm")

Download:
 [Time-Clock-0.12.tar.gz]("http://search.cpan.org/CPAN/authors/id/J/JS/JSIRACUSA/Time-Clock-0.12.tar.gz")
[Dependencies]("http://deps.cpantesters.org/?module=Time::Clock;perl=latest")

---

### Post by BastardNamban on 2009-08-03
> **&#20170 said:**
> [http://whyfiles.org/078time/](http://whyfiles.org/078time/)

Here is one in nanoseconds:

[http://search.cpan.org/~jsiracusa/Time-Clock-0.12/lib/Time/Clock.pm]("http://search.cpan.org/%7Ejsiracusa/Time-Clock-0.12/lib/Time/Clock.pm")

```
  $t = Time::Clock->new(hour => 12, minute => 34, second => 56);
  print $t->as_string; # 12:34:56

  $t->parse('8pm');
  print "$t"; # 20:00:00

  print $t->format('%I:%M %p'); # 08:00 PM

  $t->add(minutes => 15, nanoseconds => 123000000);
  print $t->as_string; # 20:15:00.123

  $t->subtract(hours => 30);
  print $t->as_string; # 14:15:00.123

```[http://search.cpan.org/~jsiracusa/Time-Clock-0.12/lib/Time/Clock.pm]("http://search.cpan.org/%7Ejsiracusa/Time-Clock-0.12/lib/Time/Clock.pm")

Download:
 [Time-Clock-0.12.tar.gz]("http://search.cpan.org/CPAN/authors/id/J/JS/JSIRACUSA/Time-Clock-0.12.tar.gz")
[Dependencies]("http://deps.cpantesters.org/?module=Time::Clock;perl=latest")

&#20170;&#24184;&#31119; (how is that pronounced, anyway? Chinese, correct? I'm a Japanese specialist btw), that might be something I can use. I will look into it.

Thanks!

---

### Post by GeneralZod on 2009-08-03
Maybe try:

```

sudo ntpdate pool.ntp.org
date +%T.%N

```

> 
The Network Time Protocol (NTP) is a protocol for synchronizing the clocks of computer systems over packet-switched, variable-latency data networks. NTP uses UDP on port 123 as its transport layer. It is designed particularly to resist the effects of variable latency by using a jitter buffer. NTP also refers to a reference software implementation that is distributed by the NTP Public Services Project.
...
NTP uses Marzullo's algorithm, and includes support for features such as leap seconds. NTPv4 can usually maintain time to within 10 milliseconds (1/100 s) over the public Internet, and can achieve accuracies of 200 microseconds (1/5000 s) or better in local area networks under ideal conditions.


[Source](http://en.wikipedia.org/wiki/Network_Time_Protocol).

---


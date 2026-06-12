---
title: "Time errors in Linux"
date: 2019-06-24
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-06-24
system calls like gettimeofday() can report an apparent resolution of one nanosecond.  that would be like incrementing at a rate of 1 GHz.  in reality PC hardware has no clock operating at such a rate.  it could be done; the hardware technology exists.  in the mean time the time reported by Linux increments at a much slower rate.

a big problem exists with this.  the time can be substantially behind when the time is gotten.  i notice this happening with a couple of clock programs, such as "dclock".  the effect is that it "misses" some seconds when the display is set to show seconds.  these programs get the time of when the clock last incremented, which can be in the previous one second period.  clocks only updating every minute might even be a whole minute off.  i've seen 15:22:59 stay for 2 seconds then jump to 15:23:01.  if that had been a one minute clock it might show 15:22 for the duration of 15:23 and look like a pretty serious bug.  i've seen a cron job think it was running on the previous day and really screw up (my workaround is those that need to know the time have a "sleep 1" before they ask for the time, or if they just need the date they don't get scheduled right at 00:00).

a program like a clock could do better by keeping (and using) it's own time value, incrementing it as needed, and calculating how long to sleep until that time is to arrive.  it could come out looking like it is ahead, so even this is not a perfect solution.  but it has done better when i have tried it.

---

### Post by kpatz on 2019-06-24
This is more an issue with an application's polling time than the actual clock resolution.  If a clock display skips seconds, it's because it's updating the display at 1 second or longer intervals.  Having it update twice a second will bring it closer to actual time, or at least the display will update once a second consistently, even if it's 1/2 second behind.

On the other hand, faster polling increases CPU usage, increasing heat and affecting battery life on laptops, though 1/2 second polling should be a negligible compared to 1 second.

I think cron sleeps a minute, then checks the time.  I would think it would always fire late, never early, so running a cron job at midnight the job should always get the correct date if it calls gettimeofday() or even the date command.

The time display on my conky updates every 5 seconds.  I guess that would drive you crazy. :)

Having your application keep its own time probably wouldn't work well either, since task scheduling isn't precise... if the CPU is busy your program might increment its second a little too late, and your clock will fall behind.  It's probably better to get the actual time from the system and then calculate the next second each time, or time your sleep so it's a bit ahead of the next second.

---

### Post by Skaperen on 2019-06-24
if the display process  wakes up and queries the time and gets an earlier time, what is it going to display?  i really have had code i wrote sleep to an expected time, query the time and get a value for a time before then.  doing this twice as often will do better as only half the period will show wrong.

i really have seen _date_ in a script scheduled by cron for 00:00:00 get 23:59:59 in the previous day.  that is what triggered all my examination of time.

for my suggested logic, right, task scheduling is not precise.  but it is *always* incremented, and task scheduling is close to where it should be.  a displayed clock *cannot* show the same time for 2 periods then jump, that way.  sure, the moment it does change might be a bit off.  but this what you'd get by over-polling, without over-polling.  it will look better and you get to see when the changes happen.

---


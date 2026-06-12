---
title: "How to read output of smartctl?"
date: 2013-12-07
forum: Ubuntu, Linux and OS Chat
---

### Post by Ck.asdf on 2013-12-07
Hello, at the recommendation of an Amazon reviewer, after purchasing a hard drive I ran smartctl -t long /dev/sda1 to ensure my drive was in proper working order, since several have been arriving DOA.

Afterward, I have run smartctl -a /dev/sda1, and the output is a bit foreign to me.

I've attached the log, but thoughts on how to read it?

Thanks!

---

### Post by ssam on 2013-12-07
```
SMART overall-health self-assessment test result: PASSED
```
so everything is good.

```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   177   177   021    Pre-fail  Always       -       4141
...
194 Temperature_Celsius     0x0022   108   098   000    Old_age   Always       -       39

```

The important column is VALUE. It will get lower if there is a problem. THRESH is the threshold where the value is considered bad. The RAW value is sometimes in useful units, but not necessarily.

So for  Raw_Read_Error_Rate, VALUE is a much bigger number than THRESH, so you are fine. In fact given that RAW is 0 there probably have never been any read errors. But you may find that some manufactures pack extra info into the raw value, like how many total reads there have been, so that could be non zero and still fine.

Spin_Up_Time is probably an actual measurement, so 4141 might mean 4.141 seconds. but it could also be different units or a set of flag values. either way VALUE is still high so everything is fine.

Temperature_Celsius, here the raw value looks like its probably in degrees C. 108 is big enough that its not an issue. the hottest the drive ever got scored 098, so its been a little bit warm than 39C at some point in its life. still not an issue.

```

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%        28         -
# 2  Extended offline    Completed without error       00%         3         -

```
someone (maybe you) ran a couple of extended tests, and the drive was fine.

[https://en.wikipedia.org/wiki/S.M.A.R.T](https://en.wikipedia.org/wiki/S.M.A.R.T). has info about many attributes and is worth a read if one of them starts to go bad.

---

### Post by Werne on 2013-12-07
There seems to be no failures or errors in the output, and there are two off-line extended self-tests ran on it, one at 3 hours lifetime (factory) and one at 28 hours lifetime (your test), both completed successfully without errors.

So it's all good, SMART reports no problems with the drive. ;)

---


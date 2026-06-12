---
title: "Laptop Battery"
date: 2008-10-12
forum: The Cafe
---

### Post by gletob on 2008-10-12
I've had my laptop for about a year now and I run my battery down about twic a week.  So I ran the built in battery learning program and my battery was built to hold 4251mAH and now it holds 4213mAH

So how do your laptop batteries fare?

---

### Post by hessiess on 2008-10-12
flatten it multiple times a day for about two years. now it only lasts about 10 munites.

---

### Post by mihai.ile on 2008-10-12
Well after 3 years mine looks like:
> 
mihai007@mihai007-laptop:~$ cat /proc/acpi/battery/BAT1/info
present:                 yes
design capacity:         4400 mAh
last full capacity:      2280 mAh
battery technology:      rechargeable
design voltage:          14400 mV
design capacity warning: 300 mAh
design capacity low:     132 mAh
capacity granularity 1:  32 mAh
capacity granularity 2:  32 mAh
model number:            ZL02
serial number:           26524
battery type:            LION
OEM info:                11        


That's about 51% of capacity and now gives me 1h10m on a full charge.
But I don't like to let the battery go down to almost 0, it is bad for LI-ION batteries.

(3 years... wow I really need to think about buying an Ubuntu XPS from Dell...)

---

### Post by Ub1476 on 2008-10-12
Around 1 month use, still 100%. I charge it when it reach 15%.

---

### Post by ankursethi on 2008-10-12
I use AC power as much as I can. MacBook batteries are impossible to get in India.

---

### Post by quanumphaze on 2008-10-12
```
:~$ cat /proc/acpi/battery/BAT1/info
present:                 yes
design capacity:         4000 mAh
last full capacity:      3482 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 300 mAh
design capacity low:     139 mAh
capacity granularity 1:  32 mAh
capacity granularity 2:  32 mAh
model number:            PRESP31
serial number:           49354
battery type:            LION
OEM info:                SANYO

```

I didn't know this info existed

This laptop was bought around Xmas 2006 and Gnome Battery thingo says it's at 87%. It could be worse, maybe I should get a new (bigger) battery before they become rare.

[EDIT] I also avoid using battery like the plague, bit drain it to about 10% at least every 10 days (is this bad for Li-ion)

---

### Post by steeleyuk on 2008-10-12
present:                 yes
design capacity:         7800 mAh
last full capacity:      7208 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 780 mAh
design capacity low:     236 mAh
capacity granularity 1:  78 mAh
capacity granularity 2:  78 mAh
model number:             DELLJN1497
serial number:           905
battery type:            LION
OEM info:                Sanyo

---

### Post by Sealbhach on 2008-10-12
Mine gives mWh rather than mAh. What does that mean? My battery only lasts about an hour. 


```
present:                 yes
design capacity:         57720 mWh
last full capacity:      57720 mWh
battery technology:      non-rechargeable
design voltage:          117600 mV
design capacity warning: 1000 mWh
design capacity low:     400 mWh
capacity granularity 1:  100 mWh
capacity granularity 2:  100 mWh
model number:            
serial number:           
battery type:            LiOn
OEM info:                Sony Corp.
```

---

### Post by Nevon on 2008-10-12
```
nevon@ubuntu:/proc/acpi/battery$ cat BAT0/info
present:                 yes
design capacity:         4400 mAh
last full capacity:      4239 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  64 mAh
capacity granularity 2:  64 mAh
model number:            M740TX
serial number:            
battery type:            LION
OEM info:                Clevo Co.
```
Just a couple of weeks old. Right now I'm in a car, but usually I run it on AC power almost all the time.

---

### Post by palamon00000 on 2008-10-12
How about this as a problem with my Inspiron 6000?

```
alarm:                   720 mAh
present:                 yes
design capacity:         7200 mAh
**last full capacity:      64933 mAh**
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 720 mAh
design capacity low:     218 mAh
capacity granularity 1:  72 mAh
capacity granularity 2:  72 mAh
model number:            DELL U48735
serial number:           11124
battery type:            LION
OEM info:                Samsung SDI
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            1 mA
remaining capacity:      3555 mAh
present voltage:         12454 mV
```

Reading a fully-charged (well... fully charged for being old) battery as being at "5% capacity" certainly annoys the crap out of me.  

Any suggestions?  Besides, you know, prayer?  :)

---


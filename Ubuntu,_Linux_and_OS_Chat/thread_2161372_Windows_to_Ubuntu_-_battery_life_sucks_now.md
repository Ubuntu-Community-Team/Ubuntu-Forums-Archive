---
title: "Windows to Ubuntu - battery life sucks now"
date: 2013-07-10
forum: Ubuntu, Linux and OS Chat
---

### Post by shovenose on 2013-07-10
Lenovo Ideapad P400 Touch laptop, Core i7 3632QM, 8GB DDR3, 1TB 5400RPM SATA, Intel HD Graphics, 14" 1600x900 Display

Suddenly battery life is much worse compared to Windows 7 and 8 both of which had about two hours more.
Any ideas why?

I've installed all Ubuntu updates and used a freshly downloaded ISO as of yesterday so I'm definitely running the latest 13.04 64-bit.

Thank you!

---

### Post by TenPlus1 on 2013-07-10
Remember that Ubuntu draws more power using the 3D Unity interface than say something like Xubuntu which uses a 2D Xfce interface and it will show in battery life...  Also you could try installing the Jupiter app that lets you manage your devices saving you on power and extending battery life...  [http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html](http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html)

---

### Post by monkeybrain2012 on 2013-07-10
> **TenPlus1 said:**
> Remember that Ubuntu draws more power using the 3D Unity interface than say something like Xubuntu which uses a 2D Xfce interface and it will show in battery life...  Also you could try installing the Jupiter app that lets you manage your devices saving you on power and extending battery life...  [http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html](http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html)

I have not benchmarked it, but I doubt that 3d Unity is the issue here, OP's Windows installation also uses desktop composting and animations (Some people seem to like to blame Unity for all kinds of things just because they don't like it) There have been many posts and blogs about Linux and battery life even long before there is Unity. The problems are apparently that certain settings are not optimized for the particular architecture of the laptops and the kernel.

Also the Jupiter applet has been discontinued for quite some times.

@OP

See if this helps
[http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html](http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html)

---

### Post by BreezyBrooke on 2013-07-10
Better power management in linux will be coming in the 3.10 and 3.11 kernels. You just have to wait till then. But at the moment battery life in linux will suck. Ubutntu 13.10 will be shipping with the 3.11 kernel so expect good battery life then.

---

### Post by monkeybrain2012 on 2013-07-10
You can install kernel 3.10 on 12.04, 12.10 or 13.04  from mainline kernel by just grabbing and installing the .debs.(headers-all headers-generic and linux-image)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-saucy/)

---

### Post by montag dp on 2013-07-10
TLP is a good power saver  choice to replace Jupiter since development of the latter has been stopped.

[http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html](http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html)

I use it on my Lenovo Thinkpad with excellent results.  Battery life is at least on par with Windows 7.  I recommend you give it a try.

EDIT: I see monkeybrain2012 has already posted this, so my post can serve as an "it works for me" type of thing.  Also, here's a quick script I wrote to monitor battery power usage.  You can run it before and after TLP to determine whether it makes a significant difference.  On my machine it does.  You may need to modify the path in the power_file variable.

```
#!/bin/bash

# Script to display system information every once in awhile


# Refresh times (in seconds)
refresh_ac=1
refresh_bat=5


# Precision for battery power
bat_prec=3


# Battery power file
power_file='/sys/class/power_supply/BAT0/power_now'


###############################################################################
# Takes raw battery power in microwatts and converts it to watts with 
# precision specified by $bat_prec
###############################################################################
battery_string (){


#  Division by 10^6
   local instring=$1
   local divpower=6
   local width=`expr length $instring`


#  Number of digits before the decimal
   local nfront=`expr $width - $divpower`


#  Rounding
   local roundidx=`expr $bat_prec`
   local roundval=${instring:$roundidx:1}
   local roundedidx=`expr $bat_prec - 1`
   local roundedval=${instring:$roundedidx:1}
   if [ $roundval -ge 5 ]; then
     roundedval=`expr $roundedval + 1`
   fi
   if [ $roundedval -eq 10 ]; then
     replacedig=2
   else
     replacedig=1
   fi


#  Put together output string
   nback=`expr $bat_prec - $nfront - $replacedig`
   local outstring=${instring:0:nfront}'.'${instring:$nfront:$nback}$roundedval


   echo "$outstring"


   }


###############################################################################
# Reads battery power in microwatts, returns battery power in watts
###############################################################################
battery_power (){
   local power_raw=`cat $power_file`
   local power=`battery_string $power_raw`
   echo "$power"
   }


###############################################################################
# Selects appropriate refresh rate for battery or ac
###############################################################################
refresh_rate (){
   local refresh=$refresh_bat
   echo "$refresh"
   }


###############################################################################
# Main program
###############################################################################


I=1
while [ $I -lt 5 ]; do


#  Read power
   power=`battery_power`


#  Print data to screen
   clear
   echo "Computer name: "`uname -n`
   echo "Linux kernel:  "`uname -r`
   echo "--------------------------------------------------"
   echo 
   echo "Battery power: $power W"


#  Wait for refresh time
   refresh=`refresh_rate`
   sleep ${refresh}s


done


###############################################################################
```

---

### Post by thiebaude on 2013-07-10
TLP works great, I have noticed a big difference .

---

### Post by shovenose on 2013-07-10
OK, I installed TLP, now what? Just let it do it's thing?

---

### Post by montag dp on 2013-07-11
You need to run:

sudo tlp start

to actually start it.  You can check its status with:

sudo tlp-stat

You can change settings if you want in /etc/default/tlp.  I think the only thing I changed in mine is the cpu mode on battery to powersave instead of ondemand.

---

### Post by linrunner on 2013-07-11
> **shovenose said:**
> OK, I installed TLP, now what? Just let it do it's thing?
Changing the config is only necessary if you want to switch radio devices (wifi, bluetooth, wwan). 

ps. **[FONT=Courier New]sudo tlp start[/FONT]** is not needed after the first reboot.

---

### Post by exploder on 2013-07-11
Giving TLP a try on my HP laptop. Thanks for the tip!

Edit: Looks better already! Starting out with 5 hours of battery life now!

---

### Post by Max Blyss on 2013-07-12
Didn't know that Jupiter was left out to dry...  I will try this 'TLP' you speak of on my Asus K52F.

Thanx for the tip, y'all.

---


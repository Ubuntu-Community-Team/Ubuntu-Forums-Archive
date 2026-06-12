---
title: "Battery not charging on Lemur in Natty"
date: 2011-06-13
forum: System76 Support
---

### Post by peperomia on 2011-06-13
I purchased a Lemur laptop (lemu2) two weeks ago. It is running fully updated Natty Narwhal 11.04. Since I purchased it, the battery symbol in the top panel has not functioned properly. When I click on the battery symbol it shows two identical lines "Laptop battery (estimating...)."  This display does not change when I unplug the laptop.

[I]More worrying: the battery does not charge. It did charge when I first got it. I am not entirely sure when it stopped charging but I think it was in the last two days after the first time I hibernated my laptop. Now when I unplug my laptop, it pops up a message "laptop battery  discharging (24)%" and the battery icon changes to red - so I can't use  my new laptop unless it's plugged in!  

[/I]CORRECTION: The battery **does** charge, just not when I'm actually using the computer. It charges when it is in 'suspend' mode. I don't know if it charges when off or hibernating (as described [here]("http://ubuntuforums.org/showthread.php?t=1687368")), but am testing that now.

Info on my battery:

sus@seventysix:/proc/acpi/battery/BAT0$ cat info
present:                 yes
design capacity:         2800 mAh
last full capacity:      2801 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
cycle count:          0
capacity granularity 1:  64 mAh
capacity granularity 2:  64 mAh
model number:            760
serial number:            
battery type:            LION
OEM info:                Clevo CO.

sus@seventysix:/proc/acpi/battery/BAT0$ cat state
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            unknown
remaining capacity:      681 mAh
present voltage:         14800 mV

---

### Post by peperomia on 2011-06-13
Like [this example]("http://ubuntuforums.org/showthread.php?t=1687368"), my laptop does charge when hibernating, suspended, or off. It does not, however, charge while I am using it. Any ideas on how to fix that?

Also, clicking on the battery icon now shows only one entry for laptop battery (estimating...), but still does not display time or % charge remaining, even when unplugged. A message does pop up when I unplug my laptop telling me % charge. I would like to replace "estimating...." with an actual time or % if possible.

---

### Post by peperomia on 2012-07-27
As in[ this thread]("http://ubuntuforums.org/showthread.php?t=1687368"), the charging problem solved itself spontaneously, making me feel like a crazy person.

---


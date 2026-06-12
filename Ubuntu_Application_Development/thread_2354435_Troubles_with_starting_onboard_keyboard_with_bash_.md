---
title: "Troubles with starting onboard keyboard with bash script"
date: 2017-03-02
forum: Ubuntu Application Development
---

### Post by rbaldinger on 2017-03-02
Hey there.

Idk if i'm right here but i try to write a little bash script for my mothers laptop with xubuntu. The problem she have is after every version update the keyboard isn't working anymore. To help her solve this problem by her self i wanted to write a small script.

```
#!/bin/bash
xfce4-terminal -e "sudo dpkg-reconfigure keyboard-configuration" &
onboard
wait
killall onboard
exit 0

```

This should open the keyboard reconfiguration assistant and the onboard keyboard for navigating and enter sudo password. 

If i run it with bash -x i get this output:
```
bash -x testrun
+ onboard
+ xfce4-terminal -e 'sudo dpkg-reconfigure keyboard-configuration'
21:36:42.063 WARNING Config: mousetweaks GSettings schema not found, mousetweaks integration disabled.

```

So it seems like the script stops after executing the onboard command. 

How can i avoid this? Or is there any better solution than reconfiguration for this problem?

Thx for help
greetings

---

### Post by rbaldinger on 2017-03-06
Used this workaround to get it work. But feels very inefficient to use 2 files to run 2 commands...

```
#!/bin/bash
#filename=testrun
script_name=$0
script_full_path=$(dirname "$0")

$script_full_path/onboard_run &
xfce4-terminal -e "sudo dpkg-reconfigure keyboard-configuration" &

while pgrep -x "xfce4-terminal" > /dev/null
do
    sleep 0.5
done

killall onboard
killall testrun
exit 0
```

and

```

#!/bin/bash
#filename=onboard_run
onboard
exit 0
```

---


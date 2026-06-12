---
title: "question on syntax to run export $DISPLAY"
date: 2009-05-06
forum: Server Platforms
---

### Post by satimis on 2009-05-06
Hi folks,


OpenVZ - Virtual Machine
host - Ubuntu 8.04
guest - Ubuntu 8.10 with wine running


On host;

$ ssh -2 -c blowfish -X satimis@192.168.0.103```

satimis@192.168.0.103's password: 
Linux vz3.satimis.com 2.6.24-24-openvz #1 SMP Wed Apr 15 19:41:36 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

```

No complaint and login guest

X forwarded to guest.

On guest

$ wineconsole cmd```

Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:wineconsole:WINECON_Fatal Couldn't find a decent font, aborting

```


$ echo $DISPLAY
only a blank line displayed.

$ export $DISPLAY=":0.0"```

-bash: export: `=:0.0': not a valid identifier

```


$ export $DISPLAY=:0.0 ```

-bash: export: `=:0.0': not a valid identifier

```


$ export $DISPLAY=0   ```

-bash: export: `=0': not a valid identifier

```

None of them can work.

Please advise what will be the correct syntax to run "export $DISPLAY"

TIA

B.R.
satimis

---

### Post by windependence on 2009-05-07
Try this:

```
DISPLAY=localhost:0.0 ; export DISPLAY
```
In bash and ksh, the syntax is to declare the variable, then export it.

-Tim

---

### Post by windependence on 2009-05-07
I found this script for your .bashrc file to set this automatically. I don't know if it works, but you could try it.

> In your .bashrc file, assuming you use bash, if you include 
the following script, the DISPLAY variable can be set up 
automatically for you each time you log on.

    # Set the DISPLAY variable handling remote logins 
    who am i | grep '(' > /dev/null
    if [ $? -eq 0 ]; then        
            # remotely logged in 
            export DISPLAY=`who am i | sed 's/.*(\(.*\)).*/\1/'`
            # Append ":0" or ":1" if not already there
            echo $DISPLAY | grep : > /dev/null
            if [ $? -eq 1 ]; then
                 export DISPLAY=${DISPLAY}:0.0
            fi                   
    fi                           
    #echo DISPLAY=$DISPLAY        


HTH,

-Tim

---

### Post by satimis on 2009-05-07
> **windependence said:**
> Try this:

```
DISPLAY=localhost:0.0 ; export DISPLAY
```
In bash and ksh, the syntax is to declare the variable, then export it.


Hi Tim,

Your advice works for me.  Thanks

satimis

---

### Post by windependence on 2009-05-07
You're welcome. You have helped me in the past and I am returning the favor. :)

-Tim

---


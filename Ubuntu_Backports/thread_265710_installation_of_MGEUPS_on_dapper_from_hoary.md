---
title: "installation of MGEUPS on dapper from hoary"
date: 2006-09-26
forum: Ubuntu Backports
---

### Post by amazilia on 2006-09-26
Hi,

I would like to install mgeups-psp on my dapper to be able to manage my ups 

On MGE website they explain how to install the package for a hoary.

when I do the install on my dapper I get the following message : 
> 
Les paquets suivants contiennent des dépendances non satisfaites :
  mgeups-psp: Dépend: libgksu1.2-0 mais il n'est pas installable
              Dépend: libgksuui1.0-0 mais il n'est pas installable
              Dépend: libglibmm-2.4-1 (>= 2.6.1) mais il n'est pas installable
              Dépend: libgtkmm-2.4-1 (>= 2.6.1) mais il n'est pas installable
              Dépend: libsigc++-2.0-0 (>= 2.0.2) mais il n'est pas installable



What should I do for get it to work 

thanks in advance

Philippe

---

### Post by Juerg on 2006-10-17
Hi Philippe,

Could you solve this issue meanwhile? If yes, please let me know how - I have exactly the same problem!

Best regards

Juerg

---

### Post by amazilia on 2006-10-18
> **Juerg said:**
> Hi Philippe,

Could you solve this issue meanwhile? If yes, please let me know how - I have exactly the same problem!

Best regards

Juerg

Hi Juerg,

No I did not. I have the feeling that now that they made their name in the linux world people from MGE do not care much about us.

I am waiting for the next version of ubuntu to see if the problem is solved.

Cheers

Philippe

---

### Post by Juerg on 2006-10-19
Philippe,

With the following change in /etc/init.d/nut  I finally got it to work. upsdrvctl needs to get started as user root and the same is true for the start-stop-daemon (see code below) The required modifications are **bold**:

```
start_stop_server () {
  case "$START_UPSD" in
    y|Y|yes|YES|Yes)
      case "$1" in
        start)
          ! /sbin/upsdrvctl **-u root** start >/dev/null 2>&1  &&  \
            echo -n " (upsdrvctl failed)"
            start-stop-daemon -S -q -p $upsd_pid -x $upsd -- **-u root** >/dev/null 2>&1          
           ;;
        stop)
          start-stop-daemon -K -o -q -p $upsd_pid -n upsd >/dev/null 2>&1
          ! /sbin/upsdrvctl stop >/dev/null 2>&1  &&  \
            echo -n " (upsdrvctl failed)"
          ;;
      esac
      ;;
    n|N|no|NO|No|*)
      return 1
      ;;
  esac
}
```

Maybe this helps others, too.

---

### Post by Juerg on 2006-10-19
I forgot to mention that I did not install the package mge-ups, instead I used the packages nut and nut-usb which are available under unbunt 6.06. (apt-get install nut nut-usb).

Good luck

Juerg

---


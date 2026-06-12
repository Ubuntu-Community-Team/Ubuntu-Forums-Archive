---
title: "Ubuntu update script with dialog"
date: 2014-03-31
forum: Ubuntu, Linux and OS Chat
---

### Post by daharibbahs on 2014-03-31
I have encounterd some people to have problems with update manager in ubuntu,so I put together this semi-userfriendly dialog script. If you find any bugs or have any suggestions please post them. Feel free to redistribute,reproduce or variate the code.

Source Code:
```

=== UPDATE.SH===
#!/bin/sh
# Depends on aptitude
# Can be distrubed or reproduced freely

a=$(sudo debconf-apt-progress -- aptitude -y update)
b=$(aptitude search ~U)

if [ -z "$b" ];
then
                dialog --backtitle "Better Ubuntu Update Script" --title "INFO" --msgbox "There are no updates avalible at this time" 15 70
                clear
                exit 0
fi

dialog --title "Are you sure you want to update?" --backtitle "Better Update Manager" --yesno "$(aptitude search ~U)" 15 70\

case $? in
        0)      sudo debconf-apt-progress -- aptitude -y upgrade
                clear
                ;;
        1)
                clear
                exit 0;
                ;;
esac

```

---


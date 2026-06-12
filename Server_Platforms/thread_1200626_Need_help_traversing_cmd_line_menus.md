---
title: "Need help traversing cmd line menus"
date: 2009-06-30
forum: Server Platforms
---

### Post by Luke has no name on 2009-06-30
I need to automate a task at work that involves starting an interactive console program; the kind where you open a menu, see a prompt, then enter the number of the menu item you need to see.

```

luke@system$: program
Entering program

1. Admin
2. Status
3. Options
4. Maintenance

luke@system$: 4

```

That sort of thing. Need to navigate multiple levels. 

1) Is this possible?

2) Would you tell me how to do it?

---

### Post by smeerbartje on 2009-06-30
> **Luke has no name said:**
> I need to automate a task at work that involves starting an interactive console program; the kind where you open a menu, see a prompt, then enter the number of the menu item you need to see.

```

luke@system$: program
Entering program

1. Admin
2. Status
3. Options
4. Maintenance

luke@system$: 4

```

That sort of thing. Need to navigate multiple levels. 

1) Is this possible?

2) Would you tell me how to do it?
I suggest you do a Google search on "bash scripting".

---

### Post by Luke has no name on 2009-06-30
As simultaneously snide and helpful that post may be, I'm using ksh.

I suppose I should look up Korn scripting.

---

### Post by sisco311 on 2009-06-30
something like:
```
PS3='Please enter your choice: '
LIST="Admin Status Options Maintenance Quit"
select OPT in $LIST
    do
        if [ $OPT = "Admin" ];
        then
            echo Admin
            break;
        elif [ $OPT = "Status" ];
        then
            echo Status
        elif [ $OPT = "Options" ];
        then
            echo Options
        elif [ $OPT = "Maintenance" ];
        then
            echo Maintenance
        elif [ $OPT = "Quit" ];
        then
            exit 0
    fi
    done

```should work in ksh.

or
```
dialog --title "Menu" \
--menu "Choose one of the following or press <Cancel>" \
15 60 4 \
"1" "Admmin" \
"2" "Status" \
"3" "Options" \
"4" "Maintenance" 2> /tmp/ans
```

for more info read:
```
man ksh # and search for select
man dialog
```

---


---
title: "login scipt based on group membership"
date: 2011-03-04
forum: Server Platforms
---

### Post by gr8day8 on 2011-03-04
I have a script I want to execute after successful login for users who are members of a specific group. 
 
Ubuntu server 64 bit, 10.04. Where could I accomplish this?
-Brian

---

### Post by t3r0 on 2011-03-04
> **gr8day8 said:**
> I have a script I want to execute after successful login for users who are members of a specific group. 
 
Ubuntu server 64 bit, 10.04. Where could I accomplish this?
-Brian

Hi,

Do the users login to gui or shell? 

- Tero

---

### Post by gr8day8 on 2011-03-04
Shell only.  BASH.

---

### Post by t3r0 on 2011-03-04
> **gr8day8 said:**
> Shell only.  BASH.


You can add something like this to bash_rc...

```

MY_GID=1000
for g in $GROUPS; do
  if [ "$MY_GID" -eq $g ]; then
    echo "Yes...."
  fi  
done

```


Just replace the echo statement with the actual command or script you want to run... 

- Tero

---

### Post by hawkmage on 2011-03-04
Here is code that will loop through the groups for a user and run a script if they are in the "adm" group:
```
for g in `/usr/bin/groups`; do
    if [ "${g}" = "adm" ]; then
        . /path_to_script 
    fi
done
```

For this to run for the user I would place the code in a file named adm_group_script.sh in the /etc/profile.d directory.

If you want it to be more generic I would create a directory /etc/group_profiles with permissions 755.  Create scripts in the directory you made named something like adm_group.sh or root_group.sh with the commands you want to run for the specific groups.  Then create a file named groups_script.sh in the /etc/profile.d directory and put his code in it:
```
for g in `/usr/bin/groups`; do
    script_file="/etc/profile.d/${g}_group.sh"
    if [ -f  ${script_file} ]; then
        . ${script_file}
    fi
done
```

---

### Post by gr8day8 on 2011-03-04
Cool! That's it!

---


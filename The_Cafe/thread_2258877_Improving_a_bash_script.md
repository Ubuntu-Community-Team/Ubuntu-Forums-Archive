---
title: "Improving a bash script"
date: 2014-12-31
forum: The Cafe
---

### Post by Tristan_Williams on 2014-12-31
I've got sort of a side project going.
I'm trying to create a bash script for use on Ubuntu systems

The script will serve as an easy-to-use menu for package management, using simple menu entries and yes/no questions.

I've gotten to one part of the script that I feel is a little dangerous, and should probably be looked over.
It could probably be optimized, safety'd, and whatever else you can do to a script.

Anyways, here it is:
```

sudo apt-get update > .ppasearch.txt
IFS=$'\n' read -d '' -r -a lines < .ppabroken.txt
cat .ppasearch.txt | grep Err | cut --characters=12- | cut --delimiter=' ' --fields=1 > .ppabroken.txt
i="0"

while [[ "${lines[$i]}" != "" ]]; do
    grep --with-filename "${lines[$i]}" /etc/apt/sources.list.d/*.list | cut --delimiter=':' --fields=1  > .pparemove.txt
    IFS=$'\n' read -d '' -r -a linesd < .pparemove.txt
    a="0"
    while [[ "${linesd[$a]}" != "" ]]; do
        file="${linesd[$a]}"
        if [ -f "$file" ]; then
            if [ -f "$file" ]; then
                sudo rm "$file"
            fi
        fi
        echo "${linesd[$a]}"
        a=$[$a+1]
    done
    i=$[$i+1]
done
rm .ppasearch.txt
rm .ppabroken.txt
rm .pparemove.txt

```

The purpose is to remove PPAs that are broken. 
Please help fix/improve this piece of the script. I'm sure to post the full script once it's done and seek further improvement

---

### Post by schragge on 2014-12-31
In event of an intermittent connectivity issue your script will happily remove any file under /etc/apt/sources.list.d/*.list if just one repository entry in that file couldn't be connected to during the apt-get update run. I'd say *a little dangerous* is an understatement.

---


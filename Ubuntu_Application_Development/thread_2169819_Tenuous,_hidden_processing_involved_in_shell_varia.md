---
title: "Tenuous, hidden processing involved in shell variable assignment"
date: 2013-08-23
forum: Ubuntu Application Development
---

### Post by odonncaoa on 2013-08-23
Greetings,

I grabbed the ANSI Escape Sequence display, present at [http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html](http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html). Upon inspection, it reflected hastily produced hackery, which offered little insight to function via commentary. And, so I cleaned it up, added some necessary insight to function, and removed the raging nonessential bits.

Notwithstanding, nestled within the algorithm is an otherwise non-imposing variable assignment, whose syntax is curious (haven't seen before); and has irritated me beyond annoyance. The statement is:
         do FG=${FGs// /}

I figured the '// /' were probably an overlooked boo-boo, which didn't hurt anything by their existence. However, upon further inspection (set -x), it became evident that the slashes presence are certainly not an overlook, and are in fact, essential. Apparently however, there are other non-obvious, additional data processing functionality at hand here. So, why doesn't the value of FG end up with a string that includes '// /' at the end, each time; instead of a properly syntaxed foreground sequence were the slashes have been eliminated? The '// /' is indispensable in eliminating an extra, non-essential whitespace in the value before the assignment becomes effective. Additionally, are there other similar types of hidden internal shell functionality available, and where might it be made obvious?

Sláinte,
[email]odoncaoa@yahoo.com[/email]

#!/bin/bash

#   set -x
#   [http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html](http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html)
#   This file echoes a bunch of color codes to the 
#   terminal to demonstrate what's available.  Each 
#   line is the color code of one forground color,
#   out of 17 (default + 16 escapes), followed by a 
#   test use of that color on all nine background 
#   colors (default + 8 escapes).
#

T='gYw'   # The test text
BGCDs="40m 41m 42m 43m 44m 45m 46m 47m"

# Output each of the background display codes being used behind each column
# across the top of the table
printf "\n        "
for    BGs    in  $BGCDs;
do    printf "  $BGs    ";
done
printf "\n"

# These are ANSI foreground codes; displayed first column (to the left & down)
for    FGx in '    m' '   1m' '  30m' '1;30m' '  31m' '1;31m' '  32m' \
          '1;32m' '  33m' '1;33m' '  34m' '1;34m' '  35m' '1;35m' \
          '  36m' '1;36m' '  37m' '1;37m'
do     FG=${FGx// /}
#do     FG=${FGx}

    # COLUMN ONLY NEEDS OUTPUT FOREGROUND CODE; REST IS REDUNDANT
    # Output the first plain foreground code text, then escaped
    # foreground code, then the fully colored test text ('gYw')
    # without fully colored background
    # echo -en " $FGx \033[$FG  $T  "
    echo   -en " $FGx"

    # Fashion a different display area, which employs a new/diff
    # foreground & background color. So, each test text ('gYw') is
    # displayed with each all foreground/background color combos
    for    BG    in  $BGCDs
    do    echo -en "  \033[$FG\033[$BG  $T  \033[0m";
    done
    printf "\n";
done
printf "\n"

set +x

---

### Post by erind on 2013-08-23
> **odonncaoa said:**
> [...]

Notwithstanding, nestled within the algorithm is an otherwise non-imposing variable assignment, whose syntax is curious (haven't seen before); and has irritated me beyond annoyance. The statement is:
do FG=${FGs// /}

[...]
The '// /' is indispensable in eliminating an extra, non-essential whitespace in the value before the assignment becomes effective. 


That's basically it - remove any whitespace present in the string **${FGs}**. It's the same concept (global replacement) you'd find in other tools such as *sed (sed 's/ //g'), awk, perl,* ...
Bash provides its own tools for the job, so no (expensive) calls are made to external tools (*sed, awk, cut, *...).

This nifty construct and more, are described in the "Parameter Substitution" section, in the same link you posted:

[http://tldp.org/LDP/abs/html/parameter-substitution.html](http://tldp.org/LDP/abs/html/parameter-substitution.html)

> Variable expansion / Substring replacement

    These constructs have been adopted from ksh.
...
 ${var/Pattern/Replacement}

    First match of Pattern, within var replaced with Replacement.
    If Replacement is omitted, then the first match of Pattern is replaced by nothing, that is, deleted.

[B][COLOR=#000000]${var//[/COLOR][COLOR=#a52a2a]Pattern[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#0000ff]Replacement[/COLOR][COLOR=#000000]}[/COLOR]

    Global replacement. All matches of Pattern, within var replaced with Replacement.
    As above, if Replacement is omitted, then all occurrences of Pattern are replaced by nothing, that is, deleted[/B].

The same thing can be found in bash man pages.

---

### Post by odonncaoa on 2013-08-28
The result certainly has functionality similar as a separate call to "sed (sed 's/ //g'), awk, perl, ..", but I hadn't stumbled upon a page which documented such reality. And, I didn't recall the existence of such a feature in the (Bourne, C, Korn, or Z) shells; although it appears that there are similar abilities in the ksh. It's a decent optimization constituent, and a good feature to be aware of. Thanks for the update. Cheers

---

### Post by sisco311 on 2013-08-28
I don't recommend the bash tutorials at tldp.org 

Parameter expansion should work in POSIX compliant shells: [http://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_06_02](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_06_02)

If you are looking for a good bash tutorial check out a the links in my signature.Parameter expansion is explained here: [http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion](http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion)


If you want to learn more about ANSI color escape sequences check out BashFAQ 037 and [http://wiki.bash-hackers.org/scripting/terminalcodes](http://wiki.bash-hackers.org/scripting/terminalcodes)

---


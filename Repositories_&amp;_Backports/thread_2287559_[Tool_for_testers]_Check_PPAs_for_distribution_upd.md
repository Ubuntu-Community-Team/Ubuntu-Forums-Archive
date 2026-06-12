---
title: "[Tool for testers] Check PPAs for distribution updates"
date: 2015-07-20
forum: Repositories &amp; Backports
---

### Post by vhaarr+launchpad on 2015-07-20
Hi,
Many years ago I found [*repostory *]("http://ubuntuforums.org/showthread.php?t=1593718")on this forum, made by a user named [Framli]("http://ubuntuforums.org/member.php?u=750404").
However, it has not been updated with a fix for changes in zenity and it  is not usable over a text terminal since it requires zenity.
So, I've stripped it down and made it easier to maintain as well.
The thread for repostory has been closed so I am making a new thread instead of replying there. I also posted this in the "Tutorials" section of the forum for ease of discovery.

Hope it helps :smile:

```
#!/bin/bash
SPAM=("http://" "ppa.launchpad.net/" "/ubuntu" ".com" "/deb")
ALL=(wily vivid utopic trusty
    saucy raring quantal precise
    oneiric natty maverick lucid
    karmic jaunty intrepid hardy
    gutsy feisty edgy dapper
    breezy hoary warty)
RELEASES=()
#RELEASES=(wily vivid utopic trusty)
# Remember that arrays start at 0. So "seq 0 3" is 4
# releases starting with the leftmost one in the array.
for i in `seq 0 3`; do RELEASES+=("${ALL[$i]}"); done

sourcesFiles=$(ls /etc/apt/sources.list.d/ | grep -v .save)
repositoryList=$(cd /etc/apt/sources.list.d && cat $sourcesFiles /etc/apt/sources.list | grep deb\ http.* | sed -e 's/.*help\.ubuntu\.com.*//' -e 's/^#.*//' -e 's/deb\ //' -e 's/deb-src\ //' -e '/^$/d' | sort -u | awk '{print $1"|"$2}' | sed -e 's/\/|/|/' -e 's/-[a-z]*$//' | uniq && cd)

for index in ${!RELEASES[@]}; do
    printf "${RELEASES[$index]^^}\t"
done
printf "REPOSITORY\n"

for repository in $repositoryList; do
    repoDistribution="$(echo $repository | sed 's/.*|//')"
    repository="$(echo $repository | sed 's/|.*//')"
    distributions=$(curl --silent $repository/dists/ | grep -oi href\=\"[^\/].*/\" | sed -e 's/href\=\"//i' -e 's/\/\"//' -e 's/-.*//' -e 's/\ NAME.*//i' | sort -u | uniq)
    if [ "$distributions" = "" ]; then
        distributions=$(curl --silent $repository/ | grep -oi href\=\"[^\/].*\" | sed -e 's/href\=\"//i' -e 's/\/\"//' -e 's/-.*//' -e 's/\ NAME.*//i' -e 's/\/index\.html\"//' -e 's/.*".*//' -e 's/http.*//' | sort -u | uniq)
    fi
    for index in ${!RELEASES
[*]}; do
        if [ $(echo "$distributions" | grep -oi "${RELEASES[$index]}") ]; then
            if [ "$repoDistribution" = "${RELEASES[$index]}" ]; then
                printf "[Yes]\t"
            else
                printf "Yes\t"
            fi
        elif [ "$distributions" = "" ]; then
            printf "?\t" # For example the google chrome repo gives us a 404
        else
            printf "No\t"
        fi
    done
    for s in "${SPAM[@]}"; do
        repository=${repository#$s}
        repository=${repository%$s}
    done
    printf "$repository\n"
done
printf "Thanks for all the fish.\n"

```

---


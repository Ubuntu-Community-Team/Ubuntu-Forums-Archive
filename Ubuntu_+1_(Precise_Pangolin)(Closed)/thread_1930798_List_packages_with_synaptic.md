---
title: "List packages with synaptic"
date: 2012-02-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dino99 on 2012-02-24
Synaptic is my prefered tool to deal with packages as its easy to find one into the differents archives. But i also should like to list the packages which are known as "suggest" or "recommend", and there synaptic seems ignoring such request.
Do you guys have something to get around that ? (i want to do some cleaning :))

---

### Post by xebian on 2012-02-24
> **dino99 said:**
> Synaptic is my prefered tool to deal with packages as its easy to find one into the differents archives. But i also should like to list the packages which are known as "suggest" or "recommend", and there synaptic seems ignoring such request.
Do you guys have something to get around that ? (i want to do some cleaning :))

Not sure exactly what you are experiencing but in Synaptics under properties you can see the suggests/recommends.

---

### Post by dino99 on 2012-02-24
> **xebian said:**
> Not sure exactly what you are experiencing but in Synaptics under properties you can see the suggests/recommends.

i'm not looking for each package, but for ALL the "suggest" installed packages. So i suppose to need a custom script for such request.
into the synaptic preferences we can check/uncheck abour the "recommended" packages to be a dependency, its nice, but nothing about the "suggested", and of course to list them after they have been installed. So on a system with rolling releases ( eg not formatted for ages), such "suggested" packages can be numerous, and i'm not sure at all that cleaning the system with deborphan or bleachbit can remove the unneeded/unwanted "suggested" packages.
thats why i'm looking, by curiosity, how i can do that.

---

### Post by elliotn on 2012-02-24
haven't seen such thing in synaptic either

---

### Post by xebian on 2012-02-24
> **dino99 said:**
> i'm not looking for each package, but for ALL the "suggest" installed packages. So i suppose to need a custom script for such request.
into the synaptic preferences we can check/uncheck abour the "recommended" packages to be a dependency, its nice, but nothing about the "suggested", and of course to list them after they have been installed. So on a system with rolling releases ( eg not formatted for ages), such "suggested" packages can be numerous, and i'm not sure at all that cleaning the system with deborphan or bleachbit can remove the unneeded/unwanted "suggested" packages.
thats why i'm looking, by curiosity, how i can do that.

Yes you need a script to do that.  It's going to be tricky.  A pkg suggested by one may be a dependency and/or recommend by another pkg.  Good luck!!!

I would suggest you go about your apps one by one and see which is least needed and start from there.  deborphan and combination of apt-get autoremove might be of help.  apt-cache show <pkg> will show suggest/recommends.  apt-cache showpkg <pkg> may also be of help.

---

### Post by dino99 on 2012-02-24
> **xebian said:**
> Yes you need a script to do that.  It's going to be tricky.  A pkg suggested by one may be a dependency and/or recommend by another pkg.  Good luck!!!

I would suggest you go about your apps one by one and see which is least needed and start from there.  deborphan and combination of apt-get autoremove might be of help.  apt-cache show <pkg> will show suggest/recommends.  apt-cache showpkg <pkg> may also be of help.

Thanks to try to find a workaround :) as you says it might be too tricky :( Will contact the synaptic devs to request these features: exclusive "suggest"/"recommend" & mixed "suggest/recommend"

---

### Post by ranch hand on 2012-02-24
Could be wrong about what you are after but if you go to Settings>Preferences>General and make sure the "Show package properties in the main window" box is checked you will get tabs in the lower horizontal pane.

One of those is dependencies.  It will list all suggested, recommended and depends for the package highlighted in the upper panel.

---

### Post by dino99 on 2012-02-24
> **ranch hand said:**
> Could be wrong about what you are after but if you go to Settings>Preferences>General and make sure the "Show package properties in the main window" box is checked you will get tabs in the lower horizontal pane.

One of those is dependencies.  It will list all suggested, recommended and depends for the package highlighted in the upper panel.

you are right, but i'm looking at the whole installed packages to sort them per "suggest" & "recommend"; the idea is to find useless "suggest" installed packages which are not detected by the usual tools (deborphan/bleachbit).

the only way i've found to collect these lists is to glance at universe/multiverse archives (synaptic's sections pane choice) but you need to review each sub category.

---

### Post by mc4man on 2012-02-24
I would think that "suggested" packages aren't installed as 'suggested', they are  'manually installed'
As such how is synaptic going to determine 'useless'

---

### Post by dino99 on 2012-02-24
> **mc4man said:**
> I would think that "suggested" packages aren't installed as 'suggested', they are  'manually installed'
As such how is synaptic going to determine 'useless'

recently some changelogs have set some previous "recommended" as "suggested" (does not really remember which packages), so "suggested" packages are not only "manually installed", even if most of the time they are indeed.

---

### Post by Harry33 on 2012-02-25
> **mc4man said:**
> I would think that "suggested" packages aren't installed as 'suggested', they are  'manually installed'
As such how is synaptic going to determine 'useless'

Synaptic classifies packages "obsolete", which are close to "useless" packages.
These are installed (not manually) packages that depend on other packages (or recommend them) or packages that some other package(s) depends on or recommends.

---

### Post by MacUntu on 2012-02-25
I'm quite sure there's no such list as you manually have to install a "Suggests"-only package, therefore tools won't see it as obsolete.

A package that is in "Suggests" of one package might as well be in "Depends" of a different package, so you'd have to take a look at the complete dependency tree:

[LIST=1]
[*]Get a list of all installed packages and all their installed "Suggests". I haven't found a way to do this via apt-cache alone, so you'd be better off with something more powerful like Python. Beware of the --installed switch of apt-cache, as it seems to mess up the output with virtual packages.
[*]For each "Suggests" package, create a list of installed packages for which they are in "Suggests". Should be simple list operations in Python.
[*]For each "Suggests" package, make sure it's installed reverse dependencies only come from the list from 2. This can be done via: ```
apt-cache --installed rdepends $pkg
``` &#8594; parse the output and check against the list.
[/LIST]

If I got more time, I'll try to hack this together.

PS: I filed two apt bug reports, which make this task unnecessarily hard: [940837](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/940837) [940848](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/940848)

---

### Post by dino99 on 2012-02-25
> **MacUntu said:**
> 940837[/url] [940848](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/940848)

Thanks for your findings and pushing that request to apt. Confirmed your reports.

---

### Post by MacUntu on 2012-02-25
Thanks. Maybe there's a way around it using aptitude, but I'm too inexperienced with that. Maybe try [http://unix.stackexchange.com](http://unix.stackexchange.com) :)

---

### Post by ranch hand on 2012-02-25
> **MacUntu said:**
> Thanks. Maybe there's a way around it using aptitude, but I'm too inexperienced with that. Maybe try [http://unix.stackexchange.com](http://unix.stackexchange.com) :)
If you are trying to get around meta package problems you can do away them and have all packages listed as manually installed using aptitude.

As root (yes I am a damned Debian user);
```

aptitude keep-all

```
This lists all packages installed as manually installed.  You could even remove the meta packages after running that but I don't know what effect that will have, in Ubuntu particularly a testing release, in your update/upgrade cycles and how dpkg stays synced with the meta package upgrades.

As all the packages are there it seems like it would make no difference.  If a new package was added to the meta package though there would be a problem.

---

### Post by mc4man on 2012-02-25
As far as aptitude you can always take a read thru or two here 
[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/)

---

### Post by ranch hand on 2012-02-25
Was just browsing the man page for dpkg and found this;
> 
EXAMPLES
       To list packages related to the editor vi(1):
            dpkg -l '*vi*'

This is certainly not a list of all packages and there related packages but it may be a help.

---

### Post by UltimateCat on 2012-02-25
I use Bleachbit and so far for the four months I have continued to use it I have never noticed nor got confirmation that it takes care of unneeded/unwanted packages.

I wish you the best on writing a script.....I'd help you but I am still learning myself about shell, ( dropping back into the shell using apt to resolve issues) bash and script-

dpkg <name of package> is a good tool for installing, removing, querying and managing  

Have a good weekend

---

### Post by effenberg0x0 on 2012-02-25
Hi, I thought what you guys are discussing is interesting: I had never thought of listing suggests and checking if they are installed. I'm aware it can be done via dpkg-query/apt-cache piped with any regexp tool in a loop. It's basically what this does, but I was in a BASH mood and wanted a CSV presentation in the output: The pipe began to get too big. 

This will export a "CSV-like" file that you can open on Calc. It has the list of packages installed on your system, the Suggests for each package, and which of these Suggests are installed. I *think* it's mostly correct, but I may very well have made many mistakes. So do not trust it's info blindly. Also, I'm aware it can be improved in many ways. But I'm hungry and sleepy now. :) 

Regards,
Effenberg


**EDIT:** If anyone is in the mood, it would be nice to make the output spreadsheet more complete, also checking and testing depends, recommends, not only suggests. But then again, if one has this and INSERT it into MySQL, how would it differ from a repo Index? LOL

$ cat get-installed-suggests.sh
```
#!/usr/bin/env bash
# Activates bash debug mode. Comment the following two lines before publishing
# releases.
set -x
set -v
#Eclipse BASH Template#####################################################START
#
# get-installed-suggests.sh
#
# A test-script to get a list of installed packages, query each package suggests and
# verify if its suggests are installed or not.
# I'm using a ';' character between fields in the output file, so that it looks
# nicely formatted in LibreOffice Calc or even MS-Excel. A Simple TXT output 
# looked too messy.
# To change it from a CSV to a "tab separated" file, change the value of the 
# variable COLUMN_SEPARATOR from CSV to TAB.
#
# USAGE: 
# $ sudo chmod +x get-installed-suggests.sh
# $ sudo./get-installed-suggests.sh 
#
# This is a BASH SCRIPT. Please don't ask me how to use it on Windows.
################################################################################
# Alvaro "Effenberg0x0" Leal <Effenberg0x0@Gmail.com> Feb, 2012
#############################################################################END

#GLOBALS
OUTPUT_DIR=.
COLUMN_SEPARATOR="csv" #You can change it to "tab" here if needed
SEP=""
OUTPUT_FILENAME=""
OUTPUT_EXTENSION=""

function defineSeparator() {
  if [[ "${COLUMN_SEPARATOR}" == "tab" ]]; then
    #echo -e "Using a tab character as column separator"
    SEP="\t"
    OUTPUT_EXTENSION="txt"    
  else
    #echo -e "Using a semi-collon character as column separator (csv format)"
    SEP=";"
    OUTPUT_EXTENSION="csv"
  fi
}

function createOutputFile() {
  local output_name=$1
  local timestamp=$(date +%d-%m-%Y_%H:%m:%S)
  
  defineSeparator
  OUTPUT_FILENAME="${OUTPUT_DIR}/${output_name}-${timestamp}.${OUTPUT_EXTENSION}"    
  #echo -e "Creating output file ${OUTPUT_FILENAME}"
  touch ${OUTPUT_FILENAME}
  if [[ $? -ne 0 ]]; then 
    echo "Error creating output file [${OUTPUT_FILENAME}]. Exiting..."
    exit 1
  else
    if [[ -e ${OUTPUT_FILENAME} ]]; then
      #echo "Output file [${OUTPUT_FILENAME}] created succesfully"
      echo -e "${OUTPUT_FILENAME}"
    else
      echo "Internal error. Exiting..."
      exit 1
    fi    
  fi
}
  

function getInstalledPackages() {
  local output_file=$(createOutputFile installed-packages)
  exec 2> >(dpkg-query -l | awk 'BEGIN {min=6} { if (NR>=min) { {FS=" "} {print $2} }}' | tee -a ${output_file}) 2>&1
  print "%s" "${output_file}" 
}

function getInstalledSuggests() {
  defineSeparator
  if [[ -z $1 ]]; then
    echo "Internal error. Exiting..."
    exit 1
  else
    local input_file=$1
  fi
  local output_file=$(createOutputFile installed-suggests)

  echo -e "Creating columns at ${output_file}"
  exec 2> >(echo -e "INSTALLED_PACKAGE"${SEP}"PACKAGE_SUGGESTS"${SEP}"INSTALLED_SUGGESTS" | tee -a ${output_file}) 2>&1
  echo -e "Querying suggests and suggest-status for each installed package from ${input_file} to ${output_file}"

  for installed_package in $(cat ${input_file}); do 
    unset pkg_suggests
    unset pkg_suggests_installed
    declare -a pkg_suggests=$(dpkg-query -W -f='${Suggests}\n' "${installed_package}" | sed -e 's| ||g' | sed -e 's|,| |g')
    for ((i=0; i<${#pkg_suggests[@]}; i++)); do
      if [[ $(dpkg-query -s ${pkg_suggests[$i]} | grep -i "Status:" | grep -i "installed" | wc -l) -eq 1 ]]; then
        pkg_suggests_installed=( "${pkg_suggests_installed[@]}" "${pkg_suggests[$i]}" )
      fi
    done
    echo -e "${installed_package}${SEP}${pkg_suggests[@]}${SEP}${pkg_suggests_installed[@]}" | tee -a ${output_file}
  done
}

function main() {
  local installed_pkgs=$(getInstalledPackages) #what a naughty boy, messing around with return values lol :P
  getInstalledSuggests "${installed_pkgs}" 
}
  
case $1 in
  *)
  main
  ;;
esac
 
```

---

### Post by dino99 on 2012-02-26
> **effenberg0x0 said:**
> Hi, I thought what you guys are discussing is interesting: I had never thought of listing suggests and checking if they are installed. I'm aware it can be done via dpkg-query/apt-cache piped with any regexp tool in a loop. It's basically what this does, but I was in a BASH mood and wanted a CSV presentation in the output: The pipe began to get too big. 

This will export a "CSV-like" file that you can open on Calc. It has the list of packages installed on your system, the Suggests for each package, and which of these Suggests are installed. I *think* it's mostly correct, but I may very well have made many mistakes. So do not trust it's info blindly. Also, I'm aware it can be improved in many ways. But I'm hungry and sleepy now. :) 

Regards,
Effenberg


Thanks for taking time to work on this whish :)
I wonder if apt-xapian-index could be usefull to sort that installed list (meaning all the installed packages, e.g. does the system already store somewhere the installed packages with tags such as "suggest" ?) (each package could have several tags indeed)

As previously said, my request will be addressed to synaptic devs, as i consider this as a feature lack.

---

### Post by MacUntu on 2012-02-26
For all installed packages that show up in "Suggests" of all installed packages, run 'aptitude why' and return the package if the "most installed, strongest, tightest, shortest" dependency chain ends with "Suggests $package":

> for pkg in $(comm -1 -2 <(dpkg --get-selections | grep -P "\tinstall$" | awk '{print $1}' | sort) <(apt-cache show $(dpkg --get-selections | grep -P "\tinstall$" | awk '{print $1}') | grep "^Suggests:\ " | sed "s/Suggests:\ //" | sed "s/\ ([^()]*)//g" | sed "s/\(,\ \|\ |\ \)/\n/g" | sort -u)); do aptitude why "$pkg" | grep "Suggests $pkg" | sed "s/.*/$pkg/"; done

Unfortunately this takes quite some time to finish (8 minutes here), but the list looks good to me. As expected, it's small and consists of mostly manually installed packages.

---

### Post by dino99 on 2012-02-26
> **MacUntu said:**
> For all installed packages that show up in "Suggests" of all installed packages, run 'aptitude why' and return the package if the "most installed, strongest, tightest, shortest" dependency chain ends with "Suggests $package":



Unfortunately this takes quite some time to finish (8 minutes here), but the list looks good to me. As expected, it's small and consists of mostly manually installed packages.

wow its great, thanks :) , will test it right now.

edit: done on Precise i386 + q9550 in 6 minutes :) Seems there is no "suggest" package installed on my system.

note: great script to bookmark.

---

### Post by effenberg0x0 on 2012-02-26
> **MacUntu said:**
> For all installed packages that show up in "Suggests" of all installed packages, run 'aptitude why' and return the package if the "most installed, strongest, tightest, shortest" dependency chain ends with "Suggests $package":
```
for pkg in $(comm -1 -2 <(dpkg --get-selections | grep -P  "\tinstall$" | awk '{print $1}' | sort) <(apt-cache show $(dpkg  --get-selections | grep -P "\tinstall$" | awk '{print $1}') | grep  "^Suggests:\ " | sed "s/Suggests:\ //" | sed "s/\ ([^()]*)//g" | sed  "s/\(,\ \|\ |\ \)/\n/g" | sort -u)); do aptitude why "$pkg" | grep  "Suggests $pkg" | sed "s/.*/$pkg/"; done

```          
Unfortunately this takes quite some time to finish (8 minutes here), but the list looks good to me. As expected, it's small and consists of mostly manually installed packages.

Hey MacUntu,

Just to give you some feedback, it was not so slow here, it took about 3 to 4 minutes at most. 

I really enjoyed your solution :) It helped me a lot. I've been playing with some scripts in which the obvious solution would be bi-dimensional arrays and "C-Like" quicksort, but emulating that in BASH is a pain.  
I had totally forgot about comm. The way you used it with sort is much more elegant and gave me a couple good ideas.

Thanks!
Effenberg

---

### Post by ranch hand on 2012-02-26
Not sure this is working right for me.   I do get a large list of packages.

First I get this though;
> 
  	 	 	 	 	 	   Warning: unknown mime-type for "%s" -- using "application/octet-stream"
     	 	 	 	 	 	   Error: no such file "%s"
   	 	 	 	 	 	   
Error: no such file "51.csv"

This did not come from an install of Ubuntu or even my Xubuntu install.  It came from my Debian testing install.


Am I missing something?  Is my system missing something?


I do get the impression that this is not going to go real well even without those errors.  I have used "aptitude keep-all" a few times on this install and I also get this;
> 
   	 	 	 	 	 	   
>   local installed_pkgs=$(getInstalledPackages) #what a naughty boy, messing around with return values lol :P
  
Just asking because this looks real handy for a number of things to me.

---

### Post by mc4man on 2012-02-26
See basically the same as RH with this script, run either as root or user no diff
Here it will end up creating 2 .csv's, 1 contains 1 column with an accurate list of all installed packages.
The 2nd  has 3 column's but no entries
(though certainly possible I'm not getting how to use..?

---

### Post by dino99 on 2012-02-26
open a terminal and copy/paste the whole command :  "for pkg .... ,done" as user, and wait a few minutes it end itself.

---

### Post by effenberg0x0 on 2012-02-26
Weird, it works for me... Are you guys using sh/dash maybe? I can't make stuff that is fully dash compatible... Try with "bash get*sh". But considering I did this thing yesterday 1AM and really fast, I'm absolutely sure it has mistakes. Actually I'm seeing them easily now and it's awful lol. But it should work anyway. I'll see into fixing it tomorrow.

Regards,
Effenberg

---

### Post by ranch hand on 2012-02-27
I am still in intense learning mode for scripts of any kind.  I stick strictly to bash.

---


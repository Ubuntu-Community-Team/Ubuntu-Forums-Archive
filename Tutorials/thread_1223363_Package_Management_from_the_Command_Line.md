---
title: "Package Management from the Command Line"
date: 2009-07-26
forum: Tutorials
---

### Post by Gen2ly on 2009-07-26
I like to work from the command line.  I found that once I got to know it, it was quicker to do the tasks that I needed to do.  Here is a quick front-end to common package management tasks that I do in Ubuntu (installing/removing packages, package information...).  It's well commented and includes help by just typing the command.  I call it **apt** and the syntax is simple:

```
apt <option> <*option2>
```

'option2' is often a package name but sometimes isn't needed.  For example:

```
apt i gimp
```

will install Gimp, and:

```
apt y
```

will sync your computer with the package repository database.  Here's the script:

```
#!/bin/bash
# Frontend for common Debian/Ubuntu package management tasks
# http://www.cyberciti.biz/ref/apt-dpkg-ref.html

# Display usage if no parameters given
if [[ -z $@ ]]; then
  echo "apt <option> <*package> - debian management tasks
  c | clean   - delete downloaded packages that are extinct (to make space)
  h | hold    - hold/freeze a package (prevent it from being updated)
  i | install - install package                (and dependencies)
  I | reinst  - reinstall package
  l | list    - list files installed by package
  L | local   - install a local package (.deb) (and dependencies)
  n | info    - package information
  o | owns    - package ownership of a file
  q | query   - lookup installed package
  Q | Query   - lookup installed package and version
  r | remove  - remove package                 (and unneeded dependencies)
  R | purge   - remove package and it's configurations
  s | search  - search for package and package description
  S | source  - download package source code and pkg creation information
  u | update  - update system
  y | sync    - sync repository database
  ---
  ppaadd      - add ppa repository
  pparem      - remove ppa repository
  ---
  Distup      - distribution upgrade
  taskinst    - add a package group
  tasklist    - list package groups
  taskpkg     - lisk packages in a group
  taskrem     - remove package group
  ---
  fixpkgman   - fix a package system that's broken (possibly, emergencies only)
  forceremove - remove package forcibly (ignore parents)
  pin         - prevent package from being installed (a.k.a. locking)
  unpin       - remove pinning (locking) of package
  rmlock      - remove package manager lock"
  exit
fi

case $1 in
  c | clean )   sudo apt-get autoclean            # rm extinct d/l pkgs
                # sudo apt-get clean              # rm all d/l pkgs (clean all?)
                sudo apt-get autoremove
                ;;
  h | hold )    shift
                echo "$@" hold | sudo dpkg --set-selections
                ;;
  i | install ) shift
                # sudo apt-get update         # Sync - bbs says here, 24 hrs?
                # sudo apt-get upgrade        # Update software
                sudo apt-get install "$@"   # Install software, here thght org
                ;;
  I | reinst  ) shift
                sudo apt-get install --reinstall "$@"
                ;;
  l | list )    shift
                dpkg -L "$@"
                ;;
  L | local )   shift
                # sudo dpkg -i "$@"
                for p in "$@"; do sudo gdebi "$p"; done
                ;;
  n | info )    shift
                apt-cache show "$@"
                ;;
  o | owns  )   shift
                dpkg -S "$@"
                ;;
  q | query )   shift
                dpkg -l | grep ^[h,i]i | awk '{print $2}' | grep "$@" 
                ;;
  Q | Query )   shift
                dpkg -l | grep ^[h,i]i | awk '{print $2"_"$3}' | grep "$@" 
                ;;
  r | remove )  shift
                sudo apt-get remove "$@" && sudo apt-get autoremove
                ;;
  R | purge )   shift
                sudo apt-get --purge remove "$@" && sudo apt-get autoremove
                ;;
  s | search )  shift
                apt-cache search "$@"
                ;;
  S | source )  shift
                apt-get source "$@"
                ;;
  u | update )  sudo apt-get update
                sudo apt-get upgrade
                ;;
  y | sync )    sudo apt-get update
                ;;
  # ---
  ppaadd )      shift
                sudo add-apt-repository "$@"
                sudo apt-get update
                ;;
  pparem )      shift
                sudo ppa-purge "$@"
                #sudo apt-get update
                ;;
  # ---
  Distup )      sudo apt-get update
                sudo apt-get dist-upgrade
                ;;
  taskinst )    shift
                sudo tasksel install "$@"
                ;;
  tasklist )    sudo tasksel --list-tasks
                ;;
  taskpkg )     shift
                sudo tasksel --task-packages "$@"
                ;;
  taskrem )     shift
                sudo tasksel remove "$@"
                ;;
  # ---
  fixpkgman )   sudo mv /var/lib/dpkg/available{,.bck}
                sudo touch /var/lib/dpkg/available
                sudo rm -vf /var/lib/apt/lists/*  # rm repo list 
              # https://wiki.ubuntu.com/ReducingDiskFootprint#Disable_apt_caches
                sudo mv pkgcache.bin{,.bck}
                sudo mv srcpkgcache.bin{,.bck}
                sudo apt-get update               # new repo list, rebuild cache
                # sudo apt-get clean
                # sudo mv /var/cache/apt /var/cache/apt-01
                ;;
  forceremove ) shift
                sudo dpkg --force-all --remove "$@"
                ;;
  pin )         shift
                for p in "$@"; do
                inst_pkg=$(apt-cache search $p | awk '{print $1}' | grep -x $p)
                  if [ -z $inst_pkg ]; then
                    echo " Package \"$inst_pkg\" appears not to exist"
                    exit
                  else
echo "
Package: "$p"
Pin: version  0.0
Pin-Priority: -1" | sudo tee -a /etc/apt/preferences
                  fi
                done
                ;;
  unpin  )      shift
                sudo sed -i "/^.*"$@"/,/-1/d" \
                /etc/apt/preferences
                ;;
  rmlock )      [ -f /var/lib/dpkg/lock ] && echo " Lock found, removing..."
                # Taking down owning app is taking down system
                #sudo fuser -cuk /var/lib/dpkg/lock; \
                #sudo rm -f /var/lib/dpkg/lock
                sudo rm -f /var/lib/dpkg/lock
                ;;
  * )           shift
                sudo apt-get "$@"
                ;;
esac
```

To have the script behave as a normal program (i.e. by typing it from the command line, you'll have to create a scripting environment.  You can read more on how to do that here:

[Setting up a Scripting Environment]("http://linuxtidbits.wordpress.com/2009/12/03/setting-up-a-scripting-environment/")

Any comments and tips appreciated.

---

### Post by Gen2ly on 2009-07-27
Oy, fixed a typo in the list line.

---

### Post by Elep.Repu on 2009-07-29
Thanks for the tip. I really couldn't find a good one, but now I have.
Good day.

---

### Post by Gen2ly on 2009-08-01
Glad you could put it to use Elep.Repu.  Danke.

---

### Post by Gen2ly on 2009-08-05
Oop, fixed some typos.

---

### Post by Gen2ly on 2009-08-17
Removed tasksel option (didn't use anyway).

---

### Post by Gen2ly on 2009-11-18
Cleaned up script a little bit more, added daemon option.

---

### Post by Gen2ly on 2010-05-01
Cleaned up script.  Nobody uses my script :(... :)... :(

---

### Post by petteriIII on 2010-05-02
But ofcourse uses, but many of us don't give feedback even if it is important. Me, for one - I read these posts reqularly to get new ideas and your post gave also some. Thanks.

---

### Post by Gen2ly on 2010-05-02
Thanks for saying such petteriIII, you made my day. :)

---

### Post by dusdus on 2010-05-03
First of all, thanks for trying and making life on the command line more convenient for all of us :)

I won't be using your script though, as I already use these options by adding aliases in my .bashrc
To be honest, I prefer it this way, as I keep a central point where I can change the terminal behaviour (I also like fancy colors in my terminal :)

Anyway, keep the good work going!

---

### Post by Gen2ly on 2011-09-22
Updated script.  Was using on a Debian system earlier and am now using Ubuntu.  Change log:

> - 'sudo' prepended for the the commands I thing that need it (pretty sure I got all of them)
- Added removing repository information and downloading new repository information to the clean command as this can sometimes become corrupted.
- Changed to gdebi to install local packages (.debs already downloaded) as it is supposedly able to check for dependencies (untested).

---

### Post by Gen2ly on 2011-10-26
Another script update.  Change log:

```
Re-ordered to better group similar tasks
Rename ppa adding and subtracting options
Fixed ppa add and subtract not always getting recognized.
```

---

### Post by Gen2ly on 2012-01-05
Script updated.  Change log:

```
Query option now only returns if package is installed; added additional 'Q | Query' option to get version information along with package name.
Reordered help description
```

---

### Post by Gen2ly on 2012-05-19
Bunch of updates: added fix package manager option, pinning, a couple bug fixes and general cleanup.  Should be good to go for about anything.

---


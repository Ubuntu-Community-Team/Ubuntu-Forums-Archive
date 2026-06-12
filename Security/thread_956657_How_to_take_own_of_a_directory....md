---
title: "How to take own of a directory..."
date: 2008-10-23
forum: Security
---

### Post by Moonfrost on 2008-10-23
I want to move a rom I have for an emulator (mame) to the roms folder, but the roms folder is in /usr/share/games/xmame/roms so that directory is owned by root, since I can't ask here how to login as root anymore I just want to know how can I take own of that directory to move the file over there? Oh, and please don't ask "why" I would want to do such a thing, thanks.

---

### Post by scragar on 2008-10-23
```
sudo chown -R $USER /user/share/games/xmame/roms
```

---

### Post by Moonfrost on 2008-10-23
> **scragar said:**
> ```
sudo chown -R $USER /user/share/games/xmame/roms
```

Thanks! I'm going to have to take note of this one because I need it often.

---

### Post by cariboo on 2008-10-23
I wouldn't really advise you change the ownership of the directory, it would be better to leave the ownership as root and just move the file using sudo eg:

```
sudo mv ~/Desktop/filename /usr/share/games/xmame/roms/
```

If you take ownerships of that directory, another user on your system will not be able to access any of the files in that directory. It is always better to do things the Linux way instead of the Windows way. Get in the habit of using sudo to do things when ever you need root access to anything.

Jim

---

### Post by scragar on 2008-10-23
hmn, what about adding a group, giving the group rights to access it, and solving the problem that way?

```
sudo groupadd Gamers ## create the group
sudo useradd -G Gamers $USER ## add you to the group
sudo chown -R root:Gamers /usr/share/games/xmame/roms ## group own the directory
sudo chmod 774 ## owner(root) and group members can edit files, others can read
```
when you log out and in again your group will own the directory, giving you

---

### Post by Moonfrost on 2008-10-23
> **cariboo907 said:**
> I wouldn't really advise you change the ownership of the directory, it would be better to leave the ownership as root and just move the file using sudo eg:

```
sudo mv ~/Desktop/filename /usr/share/games/xmame/roms/
```

If you take ownerships of that directory, another user on your system will not be able to access any of the files in that directory. It is always better to do things the Linux way instead of the Windows way. Get in the habit of using sudo to do things when ever you need root access to anything.

Jim

That's not a problem though, I'm the only user of this computer...I live alone.

---

### Post by u-slayer on 2008-10-23
I wrote a script a while back to make taking ownership, quick and easy.

```
#Change ownership of files to the `logname`

print_usage(){
	echo"
	Usage: takeover [OPTIONS] file1, file2...

	Optional:
	-u username
	-g group
	"
	exit 1
} 

#Default Options
user=`logname`

#Get Options
while getopts 'u:' OPTION
do
  case $OPTION in
  u)	user=$OPTARG;;
  g)	group=$OPTARG;;
  ?)	print_usage; exit 2;;
  esac
done
shift $(($OPTIND - 1))


if [ ! $group ]; then group=`groups $user | sed 's/ .*//'`; fi

if [ $1 ]; then
	for file in "$@"; do
		eval chown $user:$group -R "'$file'"
		eval ls -lh "'$file'"
	done
else
	chown $user:$group -R .
	ls -lh .
fi

exit 0
```

---

### Post by cariboo on 2008-10-23
The point isn't that you are the only user of the computer, it is just good computer habits, if you get in the habit of using sudo all the time. You won't make one of those mistakes that always seem to happen when you're running as root.

Just because you are the only user on the system now, you never know what will happen in the future. :)

to quote from Linux Online:

> Linux has inherited from UNIX the concept of ownerships and permissions for files. This is basically because it was conceived as a networked system where different people would be using a variety of programs, files, etc. Obviously, there's a need to keep things organized and secure. We don't want an ordinary user using a program that could potentially trash the whole system. There are security and privacy issues here as well. Let's face it, we don't want Bill to read Bob's love letters to the Janet who works in R & D. (because Janet is Bill's fiancée) In the end, it's important to know what belongs to me, to you and to everybody.


Jim

---


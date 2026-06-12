---
title: "Shutdows server using shutdown button."
date: 2008-12-09
forum: Server Platforms
---

### Post by threetimes on 2008-12-09
I have a keyboard* with a shutdown-button, and it is conected to my server.
If I press and release this button with showkeys running I get this:
showkeys -s
```
kb mode was UNICODE

press any key (program terminates after 10s of last keypress)...
0xe0 0x32 
0xe0 0xb2 
```
showkeys -k
```
kb mode was UNICODE

press any key (program terminates after 10s of last keypress)...
0x00 0x81 0xac 
0x80 0x81 0xac 
```

I think I want a little deamon running as root (or any other user able to shutdown the server), that checks for the above scancodes/keycodes and execute a script** when I release the button.

* I actually disassembled the keyboard like [this]("http://martybugs.net/electronics/kbdleds.cgi"), and the standby and shutdown buttons are the only buttons left now. The standby button doesn't generate any scancode, so I ignore it.

** The script first does a SOS and thet shuts down.
```
# first: .../---/... (morse...)
# then poweroff

# ...
echo -ne "\a"
sleep 0.2
echo -ne "\a"
sleep 0.2
echo -ne "\a"
sleep 0.6

# ---
echo -ne "\a"
sleep 0.35
echo -ne "\a"
sleep 0.35
echo -ne "\a"
sleep 0.6

# ...
echo -ne "\a"
sleep 0.2
echo -ne "\a"
sleep 0.2
echo -ne "\a"
sleep 0.6

sudo poweroff
```

---

### Post by threetimes on 2008-12-09
I got more information:

showkey -m:
```
kb mode was UNICODE

press any key (program terminates after 10s of last keypress)...
keycode   0 press
```
read:
```
^@
```

---

### Post by threetimes on 2008-12-09
Using [this]("http://www.faqs.org/docs/Linux-HOWTO/Keyboard-and-Console-HOWTO.html#s14") HOWTO i managed to type thet euro-key when I push the button
```
$ sudo setkeycodes e032 120
$ loadkeys
keycode 120 = euro
^D
```
I tried playing 'roud with bind:
```
bind -x '"\x24"':/home/peter/test.sh
```
I can now execute a script with a single press on the button.
But it only works when logged in, otherwise I just see euro-signs on the login-prompt.

A solution is to create a user with rights to shutdown the server, and nothing more. This user can automatically login when the server starts.

I'll continue google-ing...

---

### Post by threetimes on 2008-12-09
I got this working using the following scripts:
/etc/init.d/shutdown-button
```
setkeycodes e032 120
echo 'keycode 120 = Pause
string Pause = "sos-reboot\n"' | loadkeys

```So whet I press the button, or the Pause key on a normal keyboard, **sos-reboot** with a newline is printed. In a normal shell, this means that sos-reboot gets executed.

/bin/sos-reboot:
```
echo -ne "\a"
sleep 0.2
echo -ne "\a"
sleep 0.2
echo -ne "\a"
sleep 0.6

echo -ne "\a"
sleep 0.35
echo -ne "\a"
sleep 0.35
echo -ne "\a"
sleep 0.6

echo -ne "\a"
sleep 0.2
echo -ne "\a"
sleep 0.2

shutdown -r now # also produces a beep

```
For the autologin I installed mingetty:
```
sudo apt-get install mingetty
```
And in /etc/event.d/tty1 I changed this:
```
#exec /sbin/getty 38400 tty1
exec /sbin/mingetty --autologin shutdown tty1

```


The only problem is: anyone with physical access to the server can hook up any keyboard and a monitor and do anything (as a normal user) what they want.

How do I change the permissions of **shutdown** to almost nothing?
-or-
How do I automatically log this user out when a non-Pause-key is pressed?
-or-
How do I automatically switch to a different VT when a non-Pause-key is pressed.

---


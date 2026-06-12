---
title: "Game Vuln Possibility ? - Urbanterror"
date: 2012-01-29
forum: Security
---

### Post by tuxinteger on 2012-01-29
Noticed some strange anomalies during gameplay,ddos etc,file access & other access.

is this related to the ioquake3 vulns? ,please comment ,should these files be accessed by Urbanterror?.

Setup some audit logs to see what was going on,see logs below .

Whilst playing files such as tcpdump ,firefox,& /etc/passwd are  being accessed ,and denied ,but access request is via the urbanterror  application appears to be piped through nvidiactl .

This occurs on some servers ,not all ,and there seems to be some chat in regards to these activities .

Thought this had been corrected ?,no guru but these files shouldnt be  accessed by the UT executable,one slip on an unpatched system and Valla  ,root access via the app,looks like smurfing was attempted.


Include Evince & thumbnailer


type=AVC msg=audit(1326506857.797:109): apparmor="DENIED"  operation="open" parent=1  profile="/home/user/Downloads/UrbanTerror/ioUrbanTerror.i386"  name="/etc/passwd" pid=6333 comm="ioUrbanTerror.i" requested_mask="r"  denied_mask="r" fsuid=1006 ouid=0
type=AVC msg=audit(1326544741.665:463): apparmor="DENIED"  operation="open" parent=1  profile="/home/user/Downloads/UrbanTerror/ioUrbanTerror.i386"  name="/etc/passwd" pid=10378 comm="ioUrbanTerror.i" requested_mask="r"  denied_mask="r" fsuid=1006 ouid=0
type=AVC msg=audit(1326590224.799:58): apparmor="DENIED"  operation="open" parent=1934  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=1937 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1326590767.580:59): apparmor="DENIED"  operation="open" parent=2117  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=2120 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1327574589.468:58): apparmor="DENIED"  operation="open" parent=2150  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=2153 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1327583606.594:62): apparmor="DENIED"  operation="open" parent=10865  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=10868 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1327584249.739:61): apparmor="DENIED"  operation="open" parent=2123  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=2126 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1327584461.401:62): apparmor="DENIED"  operation="open" parent=2247  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=2250 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1327624066.389:61): apparmor="DENIED"  operation="open" parent=1930  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=1933 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1327625263.922:62): apparmor="DENIED"  operation="open" parent=2107  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=2110 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1327628694.351:63): apparmor="DENIED"  operation="open" parent=2284  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=2287 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1327631742.656:64): apparmor="DENIED"  operation="open" parent=2448  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=2451 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1327632687.132:65): apparmor="DENIED"  operation="open" parent=2555  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=2558 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1327636142.949:66): apparmor="DENIED"  operation="open" parent=2690  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=2693 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1327636151.389:67): apparmor="DENIED"  operation="open" parent=1  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=2690 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1327651089.657:68): apparmor="DENIED"  operation="open" parent=1  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=3027 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1327651097.821:69): apparmor="DENIED"  operation="open" parent=3085  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=3087 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1327652654.838:70): apparmor="DENIED"  operation="open" parent=4526  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=4529 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1327652954.244:71): apparmor="DENIED"  operation="open" parent=4567  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=4570 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1327653960.215:72): apparmor="DENIED"  operation="open" parent=4995  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=4998 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1327654194.069:73): apparmor="DENIED"  operation="open" parent=5436  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=5439 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1327658238.106:75): apparmor="DENIED"  operation="open" parent=1  profile="/home/user/Downloads/UrbanTerror/ioUrbanTerror.i386"  name="/etc/passwd" pid=5931 comm="ioUrbanTerror.i" requested_mask="r"  denied_mask="r" fsuid=1006 ouid=0
type=AVC msg=audit(1327658599.113:76): apparmor="DENIED"  operation="open" parent=5959  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=5962 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1006 ouid=0
type=AVC msg=audit(1327658913.385:77): apparmor="DENIED"  operation="open" parent=6019  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=6022 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1006 ouid=0
type=AVC msg=audit(1327659728.159:78): apparmor="DENIED"  operation="open" parent=1  profile="/home/user/Downloads/UrbanTerror/ioUrbanTerror.i386"  name="/etc/passwd" pid=6072 comm="ioUrbanTerror.i" requested_mask="r"  denied_mask="r" fsuid=1006 ouid=0
type=AVC msg=audit(1327667382.139:79): apparmor="DENIED"  operation="open" parent=7204  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=7207 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1327670997.354:80): apparmor="DENIED"  operation="open" parent=1  profile="/home/user/Downloads/UrbanTerror/ioUrbanTerror.i386"  name="/etc/passwd" pid=7522 comm="ioUrbanTerror.i" requested_mask="r"  denied_mask="r" fsuid=1006 ouid=0
type=AVC msg=audit(1327671737.173:81): apparmor="DENIED"  operation="open" parent=7574  profile="/home/user/Downloads/UrbanTerror/ioUrbanTerror.i386"  name="/etc/passwd" pid=7575 comm="ioUrbanTerror.i" requested_mask="r"  denied_mask="r" fsuid=1006 ouid=0
type=AVC msg=audit(1327671738.249:82): apparmor="DENIED"  operation="mknod" parent=7574  profile="/home/user/Downloads/UrbanTerror/ioUrbanTerror.i386"  name="/home/user/Desktop/botlib.log" pid=7575 comm="ioUrbanTerror.i"  requested_mask="c" denied_mask="c" fsuid=1006 ouid=1006
type=AVC msg=audit(1327705036.132:58): apparmor="DENIED"  operation="open" parent=2052  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=2055 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1327725678.568:59): apparmor="DENIED"  operation="open" parent=3292  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=3295 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1327747606.120:61): apparmor="DENIED"  operation="open" parent=2048  profile="/usr/lib/firefox-9.0.1/firefox{,*[^s][^h]}"  name="/dev/nvidiactl" pid=2052 comm="firefox" requested_mask="rw"  denied_mask="rw" fsuid=1000 ouid=0
type=AVC msg=audit(1327757342.736:62): apparmor="DENIED"  operation="open" parent=1  profile="/home/user/Downloads/UrbanTerror/ioUrbanTerror.i386"  name="/etc/passwd" pid=3043 comm="ioUrbanTerror.i" requested_mask="r"  denied_mask="r" fsuid=1006 ouid=0
type=AVC msg=audit(1327762005.656:63): apparmor="DENIED"  operation="open" parent=1  profile="/home/user/Downloads/UrbanTerror/ioUrbanTerror.i386"  name="/etc/passwd" pid=3335 comm="ioUrbanTerror.i" requested_mask="r"  denied_mask="r" fsuid=1006 ouid=0

---

### Post by OpSecShellshock on 2012-01-29
It looks like the Firefox events are actually being caused by Firefox itself, so that's a separate issue. My guess is it has something to do with the hardware acceleration feature. That can be disabled in Preferences under Advanced, General tab, then in the Browsing section. I would suggest that you uncheck that box and run Firefox again, then check the same logs to see if the apparmor events go away.

The other application I'm not sure about.

EDIT: I just noticed that the UrbanTerror is located in the Downloads folder. Is it not actually installed? Where was it downloaded from?

---

### Post by Dangertux on 2012-01-29
As the poster above me stated Firefox graphical acceleration is what's causing the majority of these.

The issue with Urban Terror trying to access /etc/passwd is because Urban Terror locks the passwd file at run time, it will retry if it fails (like if Apparmor is not allowing it). 

/etc/passwd is world readable and accessible to most applications, it is not odd to see them attempting to access it. As far as smurfing, not sure where you are determining from that log that a denial of service of that nature is being attempted, as it is an Apparmor audit log and a smurf attack does not attempt to access objects on the disk. It instead attempts to send surrupticious amounts of ICMP echo requests to the target (hence it's nickname the ping of death). 

It is easy enough to deny that traffic if you are seeing it. 

```

sudo iptables -A INPUT -p icmp --icmp-type 8 -j DROP

```In this case I think the root cause of the logs is quite simply a misconfigured apparmor profile.

---

### Post by tuxinteger on 2012-02-01
Ok cheers . that explains the /etc/passwd .

I will also try the settings recommended by [OpSecShellshock]("http://ubuntuforums.org/member.php?u=946893") for graphics control .

Downloaded from Urban Terror site mirror .

The ddos seemed to be caused in the game and network bandwidth being swallowed along with
file access ,the firefox bit sent things off on a tangent i suppose.

Sorry i had grepped the logs,and there is some concatenation ,firefox libs are called by the game 
exe Urbanterror,i dont have original logs at the very present,i will post when i get back to that machine.

So its possible with firefox not loaded that the game exe would need to access it or is it some form 
of game nvid control combined with firefox ?.

  I did have the logs where tcpdump was accessed while playing ,and was successfully accessed.

I should also add that severe traffic interruption was experienced ,before i changed the apparmour config for the executable.

The gents who originally located the vuln in quake3 say it does look like the vuln they found 5 years ago,
bugtraq/2006-05/msg00168.html 

I have had people say they have accessed the file system under the user group playing the game ,via a console .
& BTW I'am not running as root or su group,this is strange as this a udp game (socks disabled) ,unless there is some code
in it that opens ,but normal net utils arent showing any tcp sockets.


Thanks for the suggestions .

---


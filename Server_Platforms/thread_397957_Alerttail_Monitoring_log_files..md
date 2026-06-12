---
title: "Alerttail: Monitoring log files."
date: 2007-03-31
forum: Server Platforms
---

### Post by kimbuba on 2007-03-31
Hello we have just released an open project: Alert tail


Alerttail executes actions when "some text" has been written to a file.
This software tails a file and when a line matches some text pattern alerttail will execute a list of actions defined on it's own configuration file.

Imagine you want to be warned when some text is written to a log file, you could just configure alerttail asking it to notify you with a gtk notify popup.

For example when i start my proftpd server for desktop file sharing i would like to monitor when somebody logs in and downloads a file. To know that i would configure alerttail to analyse /var/log/proftpd/proftpd.log and /var/log/proftpd/xferlog.

Or if i would like to know when somebody execute a "su" command i will configure alerttail to listen to /var/log/auth.log.

Same thing for samba access, kernel , mail, gaim events or any other log file event.

Another interesting scenario is iptables monitoring. If we want to know if a remote host try to direct connect to our box we will ask alerttail to monitor /var/log/messages and alert us with a notify popup with a link to googleMaps for GeoIp Localization.


How does it works:
Alerttail is configured via config files.
Each file will define tail match policies.
When it tails a file, each line is parsed by a regular expression agent that will determine if that text line matches a provided text pattern. If it does, it will execute several actions defined by the user.

Each tailed file can have one or more regex parsers and each of those parsers will trigger one or more actions.
Actions can be alerttail built in actions (GTK notify action , geoipLocalization action, filtering text action) or a custom user defined shell command action.


Alerttail has been developed in C++ for linux platform.


If you find this interesting please visit [http://alerttail.sourceforge.net/]("http://alerttail.sourceforge.net/")

hope you guys will find this useful.
Any feed back is welcomed.
Thank You.

---

### Post by revertex on 2007-04-29
pretty cool, but a bit complicated to config.

---

### Post by kimbuba on 2007-04-30
yes i know.
that's because of config file configuration format: easy to program with but hard to edit by hand.
A gui will be provided (wxwidgets).

how do you use it?
iptables? auth? proftpd?

with notify popup?


do you have any suggestions?

Thank you.

---

### Post by revertex on 2007-04-30
Actually, iptables with notify popup.

Alertail is amazing, i see a great potential as notifier for events that happen in realtime, much like some windowze firewall do.

I know that linux can be secure as hell, but is really nice to know if someone is attempt to ssh against my box, or accessing my  webserver.

also it should be a great tool to be sure that you don't did any mistake configuring a firewall or mail server.

I haven't time enough to play with it, but i want to write a cfg to notify me when someone access my thttpd server.

Being OSS i think it's just a metter of time to more people discover it and start contributing with more config files.

A dozen of different config files will be enough to cover all kind of logs under the sun i guess.

just a little question, what it uses to watch for file changes, something like gamin or inotify?

---

### Post by kimbuba on 2007-05-01
Thanks for your interest revertex.
Watching files is delegated to a custom tailing monitor.
It just tails a file every N seconds and consumes text.
I wanted to minimize unnecessary dependencies.

Maybe a gui will make alerttail more attractive to intermediate (or lazy) users.
The problem is that Regular expression are hard to master, so i will need to create less powerful but easier pattern language (like thunderbird filters).

If you make a cfg file for httpd page access monitoring let me know as i will add it to example provided files.

Thank you,
Kim.

---

### Post by kimbuba on 2007-09-02
Hello,
we have released  alertTail GUI.
We hope it will help people in configuring alerttail cfg files.

For those who are interested you can download it from here: 

[http://alerttail.sourceforge.net/]("http://alerttail.sourceforge.net/")

Thank you,
Kim,

---

### Post by tlepes on 2008-02-25
Are there [any plans for] x86_64 debs?  I have an AMD 64 X2 running Ubuntu 7.10.

I am also curious if anyone is using it to monitor logs on a remote server and how they go about it?  I would guess mounting the server's /var/log dir to a mountpoint on the desktop where the alerts will be shown?

Maybe a future enhancement would be to run the tail on a server but send the alerts to a desktop client?

All and all it looks like a great program.  I am going to try installing from source if I can't find an Ubuntu .deb for amd64.

Peace,
Tim

---

### Post by kimbuba on 2008-02-25
Hi Tim,
i'am gald to know you found Alerttail useful.

There are no debs for x86_64 arch yet.
You can try to build by your own and asking me if you encounter any troubles.

There is no client / server alertTail implementation, thought it would be interesting and challenging implementing it.

You can have a client-server behaviour with this work-around:
you can play with netcat.

The base idea is that on server side alertTail will match and echo text to a file. That file will be tailed by netcat and redirected to a client host machine which in its turn it will append to an alertTail tailed file.

**Client Side (where u want desktop custom notifications):

[PHP]
netcat localhost -l -p 9001 >> result.log
//then apply alertTail to that file as usual
//i.e. alertTail -c myFileOnResult.cfg
[/PHP]

result.log will contains server side matching logging text.
You will configure alertTail as usual with this file (se below to know where its contents come from)

**Server Side (where your app logs):

Create this alerttail file config.
Basically it will echo matching text into his internal logging 

echoAlert.cfg:
[PHP]
file : 
{
  fileName = "/var/log/messages";
  sleepSeconds = 2;
  textFallDown = false;
};
log : 
{
  fileLevel = "INFO";
  filePath = "./mylogs.log";
};
parser : 
{
  parsers = ( 
    {
      type = "regexParser";
      pattern = ".*APATTERN.*";
      actions = ( );
    } );
};
[/PHP]

Where APATTERN is a custom matching pattern.
This will only log matching text into mylogs.log (relative to it's current working dir).

then execute those commands:

[PHP]
alertTail -c echoAlert.cfg & && tail -f mylogs.log | netcat 192.168.1.2 9001
[/PHP]

In this way you are executing alertTail telling it to append matching text into it's internal logging file mylogs.log. by the same time you are tailing that file sending all it's contents to your client host (ip 192.168.1.2 in this example) which will then apply another alertTail execution.


Hope it helps.
Greetings,
Kim

Could you please give me any feedbacks regaring alertTail and alertTail GUI? That would be great.

---


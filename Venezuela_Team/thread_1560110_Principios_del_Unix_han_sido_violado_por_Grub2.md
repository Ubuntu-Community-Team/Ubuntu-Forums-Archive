---
title: "Principios del Unix han sido violado por Grub2"
date: 2010-08-24
forum: Venezuela Team
---

### Post by galanh on 2010-08-24
Hay 5 principios del Unix.
 

 Estoy sospechado que los panas de Grub2 rompieron el pricipio que dice:
 "Programas Pequeños de una sola tarea"


Tambien vilolaron el principio que dice:
"Que tu programa haga por lo menos una cosa bien"

 

 Grub2 es un camastron grande y viene Windown y suaaazzz lo apaga.
 Porque al antiguo Grub (que ahora pasó a ser Legado) no le pasaba tanto eso?
 

 Pues si, estoy en guerra contra el Grub2
 Ver el hilo denominado:
 Window7 desinstala mi boot loader
 A lo mejor no es solo Window, tambien esta la particion de Dell
 que ya borre.

---

### Post by galanh on 2010-08-25
Por fin tengo ¨dual boot” (SOLVED)

 

 Queria contarles como logre acabar con los programas de Dell,  
 que me hicieron perder tanto tiempo. En dos platos:  
 primero les elimine su particion y luego los des-instalé.
 

 Lo primero que aprendí por via de los golpes es que si  
 tu computador te dice:
 Operating System not found
 Hay que sonreir y decirse a si mismo las instalaciones y particiones  
 estan ahi, solo hay que reparar el Grub2 con el LiveCD.
 

 Durante la ultima instalacion de Lucy Lyxn que realizé, 

 solicité borrar la particion:
 /dev/sda1 63	80,324		de	Dell Utility
 De esta forma elimine la casita de Dell muy cercana al MBR.
 

 La particion liberada /dev/sda1 fue tomada por la particion Extended  
 que engloba las dos particiones de Linux.
 Luego al terminar la instalacion tienes un solo tiro para entrar en Window7  
 y desinstalar el recovery y el backup de Dell.
 

 Cuando sales de window ya el daño lo han causado antes de la desinstalacion.
 Pero no importa, vuelves a reparar el Grub2 y la historia termino.
 Mas nunca mas vuelves a ver el mensaje: Operating System not found
:KS

---

### Post by galanh on 2010-08-28
En este hilo, mas arriba, se da una solucion particular que
funciona ya que el problema mas nunca lo he visto.

En el siguiente articulo se esta buscando la solucion general:

```

   	 	 	 	 	 	  Sat, 28 Aug 2010  **Windows applications making GRUB 2 unbootable**

 
  If you find that running Windows makes a GRUB 2-based system unbootable ([Debian bug]("http://bugs.debian.org/550702"), [Ubuntu bug]("https://bugs.launchpad.net/bugs/441941")),  
then I'd like to hear from you.  
This is a bug in which some  proprietary Windows-based software overwrites particular sectors in the  gap 
between the master boot record and the first partition, sometimes  called the "embedding area".  
GRUB Legacy and GRUB 2 both normally use  this part of the disk to store one of their key components: 
GRUB Legacy  calls this component Stage 1.5, while GRUB 2 calls it the core image ([comparison]("http://www.gnu.org/software/grub/manual/grub.html#Images")).   
However, Stage 1.5 is less useful than the core image (for example,  the latter provides a rescue shell which 
can be used to recover from  some problems), and is therefore rather smaller: somewhere around 10KB  vs. 24KB 
for the common case of ext[234] on plain block devices.  
It  seems that the Windows-based software writes to a sector which is after  the end of Stage 1.5, but before the 
end of the core image.  This is why  the problem appears to be new with GRUB 2.

  At least some occurrences of this are with software which writes a  signature to the embedding area which hangs around even after  
uninstallation (even with one of those tools that tracks everything the  installation process did and reverses it, I gather), so that you cannot  
uninstall and reinstall the application to defeat a trial period.  This  seems like a fine example of an [antifeature]("http://wiki.mako.cc/Antifeatures"),  especially given its 
destructive consequences for free software, and is  in general a poor piece of engineering; what happens if multiple such  programs want to 
use the same sector, I wonder?  They clearly aren't  doing much checking that the sector is unused, not that that's really  possible anyway. 
 While I do not normally think that GRUB should go to  any great lengths to accommodate proprietary software, this is a case  where we need 
to defend ourselves against the predatory practices of  some companies making us look bad: a relatively small number of people  do enough 
detective work to realise that it's the fault of a particular  Windows application, but many more simply blame our operating system  because it 
won't start any more.
  I believe that it may be possible to assemble a collection of  signatures of such software, and arrange to avoid the disk sectors they  have stolen. 
 Indeed, I have a first draft of the necessary code.  This  is not a particularly pleasant solution, but it seems to be the most  practical way around 
the problem; I'm hoping that several of the  programs at fault are using common "licence manager" code or something  like that, so that we can 
address most of the problems with a relatively  small number of signatures.  In order to do this, I need to hear from  as many people as possible 
who are affected by this problem.
  If you suffer from this problem, then please do the following:
  
 
[LIST]
[*]Save the output of fdisk -lu to a 	file.  In this  output, take note of the start sector of 	the first partition (usually  63, but might also be 2048 
[*]on 	recent installations, or occasionally  something else).  If 	this is something other than 63, then replace 63 in  the 	following items with your number.
[*]Save the contents of the embedding 	area to a file (replace /dev/sda with your disk device if it's 	something else): dd if=/dev/sda of=sda.1 count=63
[*]Do whatever you do to make GRUB 	unbootable (presumably starting  Windows), then boot into a 	recovery environment.  Before you reinstall  GRUB, save 	the new contents of the embedding area to a different file: dd 	if=/dev/sda of=sda.2 count=63
[*]Follow up to either the Debian or the Ubuntu bug with these 	three files (the output of fdisk -lu, and the embedding area before 	and after making GRUB unbootable.
[/LIST]
  I hope that this will help me to assemble enough information to fix  this bug at least for most people, and of course if you provide this  information then I can make sure to fix your particular version of this  problem.  Thanks in advance!
 

```

---

### Post by galanh on 2010-08-29
La solucion no es buscar culpables.

Este personaje de internet expresa muy bien como un error en Grub2 le siguie 
otro error en window7 y despues le sigue otro error en las aplicaciones de Dell y HP:

```

[COLOR=#000000]I think the application is  clearly at fault here. 
The boot loader doesn't have to make any  assumptions about the disk 
(not even the presence of files or a  filesystem), it sets up the info passed 
on to the operating system and  both the operating system *and* any applications 
within that OS should stay outside of areas that were not explicitly allowed. 
The OS  should never allow an application to do this.[/COLOR]

```

[http://news.ycombinator.com/item?id=1643451](http://news.ycombinator.com/item?id=1643451)

---

### Post by rimjim on 2012-04-06
Travesti chatroulette chat roulette  Türkiye'nin ilk Travestiler'e yönelik online 

chat roulette  sohbet ve chat sitemiz çok yakinda.Travesti Best Model üyeleri 

sohbet odalari chat kanallar'inda diger ü…
____________________________________________________________________
[Travesti.](http://www.travestibestmodel.net/)

---


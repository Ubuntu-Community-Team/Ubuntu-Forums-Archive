---
title: "runing Bristol with Jack"
date: 2008-10-31
forum: Ubuntu Studio
---

### Post by Capoeira on 2008-10-31
it doesn't work. Bristol without Jack is working. But "startBristol -jack" with Jack running returns to this:

--------------------------------

capoeirista@Capoeira:~$ startBristol -jack
        You may want to make bristolengine a suid-root executable
spawning midi thread                                             
        flags are 8a000000                                       
midi sequencer                                                   
Returning socket 3                                               
Opened listening control socket: 5028                            
connected to :0.0 (9afb2f0)                                      
display is 1024 by 768 pixels                                    
Window is w 1024, h 768, d 24, 0 0 0                             
Using TrueColor display                                          
Client ID = 128                                                  
masks are ff0000 ff0000 ff0000                                   
Queue ID = 0                                                     
Device name did not parse, defaults 128.0                        
Found 1 descriptor                                               
Could not reschedule thread to 2                                 
parent going into idle loop                                      
INIT: 9afb008                                                    
Initialise the mini link to bristol: 9b01fa8                     
hostname is localhost, bristol
port is 5028
acceptConnection(0)
Accepted connection from 0 (3) onto 2 (6)
Connected to the bristol control socket: 6
bristolengine already active
80d4e80 80000000 0
bristolSystem(127, 0, 64) 10
        flags are 2010
configured 16 voices
message from 2, 0
bristolSystem(127, 0, 14) 0
        flags are 700
2:      2 2
configuring midi channel to 0
bristolSystem(127, 0, 2) 0
        flags are 100
going to attempt engine kickoff: 2000 (-1)
spawning audio thread
init audio thread, 80c5c40
bufsize is now 1024
bristolAudioOpen(/dev/audio, 44100, 1024, 8a000004)
audioOpen(080944a0, 0, 1024): /dev/audio
flags are now 2
Failed to open audio device "/dev/audio", flags 2
Problem opening audio device /dev/audio, exiting audio thread
Could not get thread schedule
bristolSystem(127, 0, 12) 0
        flags are 600
1:      2 2
initialising one bristolmini
return - no data in buffer
cleanupBristol(0)
/usr/bin/startBristol: line 130: 24601 Falha de segmentação  bristolengine -preload 4 -bufsize 1024 $audioflags $midiflags $*
capoeirista@Capoeira:~$

-----------------------------

---


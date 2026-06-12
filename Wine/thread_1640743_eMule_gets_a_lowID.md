---
title: "eMule gets a lowID"
date: 2010-12-08
forum: Wine
---

### Post by Mikywing on 2010-12-08
Hi all! I have to ask you people for some help about eMule 0.50a running with wine 1.2 on Ubuntu 10.04LTS Lucid Lynx 64bit.

I installed wine 1.2 beta (which btw has become final) from the official lucid repos, and eMule 0.50a. I used to do so in the past, but now i can't realize why i can't get a HighID, which is needed to get optimal performance while sharing.
I configured eMule as usual (TCP port is 54321 and UDP is 54320), i use a static IP (192.168.0.1) and my router is correctly set to forward those ports to that IP. This setup always worked in the past, i can't realize why now it doesn't.
I also tried to manually open the ports in Ubuntu with the commands:
```
sudo ufw allow 54321/tcp
sudo ufw allow 54320/udp
sudo ufw enable

```
But it hasn't been useful.

This is the output i get while running emule from terminal:
```
wingman@Sandiego:~/.wine/drive_c/Programmi/eMule$ wine emule.exe 
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),4,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {5c63c1ad-3956-4ff8-8486-40034758315b} not registered
err:ole:CoGetClassObject class {5c63c1ad-3956-4ff8-8486-40034758315b} not registered
err:ole:create_server class {5c63c1ad-3956-4ff8-8486-40034758315b} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {5c63c1ad-3956-4ff8-8486-40034758315b} could be created for context 0x17
[B]err:winediag:WSASocketW Failed to create a socket of type SOCK_RAW, this requires special permissions.
err:winediag:IcmpCreateFile Failed to use ICMP (network ping), this requires special permissions.[/B]
err:listview:LISTVIEW_WindowProc unknown msg 108a wp=00000000 lp=0032c994
fixme:richedit:ME_HandleMessage EM_GETLANGOPTIONS: stub
fixme:richedit:ME_HandleMessage EM_SETLANGOPTIONS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_GETLANGOPTIONS: stub
fixme:richedit:ME_HandleMessage EM_SETLANGOPTIONS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_GETLANGOPTIONS: stub
fixme:richedit:ME_HandleMessage EM_SETLANGOPTIONS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:shell:IAutoComplete2_fnInit  ACO_FILTERPREFIXES not supported
err:listview:LISTVIEW_WindowProc unknown msg 108a wp=00000000 lp=0032cab0
err:listview:LISTVIEW_WindowProc unknown msg 108a wp=00000000 lp=0032cae4
err:listview:LISTVIEW_WindowProc unknown msg 108a wp=00000000 lp=0032cac8
err:listview:LISTVIEW_WindowProc unknown msg 108a wp=00000000 lp=0032cac8
err:listview:LISTVIEW_WindowProc unknown msg 108a wp=00000000 lp=0032cac8
err:listview:LISTVIEW_WindowProc unknown msg 108a wp=00000000 lp=0032cac8
err:listview:LISTVIEW_WindowProc unknown msg 108a wp=00000000 lp=0032cac8
err:listview:LISTVIEW_WindowProc unknown msg 108a wp=00000000 lp=0032cac8
err:listview:LISTVIEW_WindowProc unknown msg 108a wp=00000000 lp=0032cac4
err:listview:LISTVIEW_WindowProc unknown msg 108a wp=00000000 lp=0032cac4
fixme:shell:IAutoComplete2_fnInit  ACO_FILTERPREFIXES not supported

```
I find interesting the line (which i marked bold) where it tells me it's unable to create a raw socket because of permissions.

I even tried to run with sudo (ubuntu prevents me to do so) and with different wine versions (also took from unofficial wine repos) but i got the same results.

Anyone knows what's happening? Anyone can help me? :)

---


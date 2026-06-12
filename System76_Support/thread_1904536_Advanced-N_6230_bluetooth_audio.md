---
title: "Advanced-N 6230 bluetooth audio"
date: 2012-01-04
forum: System76 Support
---

### Post by jschall1 on 2012-01-04
I have a gazelle professional (gazp6) with an intel advanced-n 6230 wifi/bt adapter (8086:0189 Intel Corp.) and a pair of bluetooth headphones (rf-mab2) which I cannot get to connect with the internal bluetooth. I also cannot transfer a file to my android phone. I can do both of these things just fine with my USB wifi adapter.

I'm listing syslogs from trying to connect my headphones below, as they are my main concern. I can provide any additional information necessary.

I'm running Kubuntu 11.10 with the s76 driver installed.

syslog after pressing Fn-F12: 
```
jschall@jon-laptop:~$ diff /var/log/syslog ~/syslog
5239,5245d5238
< Jan  4 19:50:23 jon-laptop kernel: [  424.760398] usb 2-1.4: new full speed USB device number 7 using ehci_hcd
< Jan  4 19:50:23 jon-laptop bluetoothd[1143]: HCI dev 0 registered
< Jan  4 19:50:23 jon-laptop bluetoothd[1143]: Listening for HCI events on hci0
< Jan  4 19:50:24 jon-laptop bluetoothd[1143]: HCI dev 0 up
< Jan  4 19:50:24 jon-laptop bluetoothd[1143]: input-headset driver probe failed for device 20:13:E0:68:08:BA
< Jan  4 19:50:24 jon-laptop bluetoothd[1143]: Adapter /org/bluez/1143/hci0 has been enabled
< Jan  4 19:50:24 jon-laptop pulseaudio[1807]: [pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod
```

syslog after connecting headphones to internal bt
```
jschall@jon-laptop:~$ diff /var/log/syslog ~/syslog
5246,5253d5245
< Jan  4 19:51:30  pulseaudio[1807]: last message repeated 2 times
< Jan  4 19:51:30 jon-laptop bluetoothd[1143]: Badly formated or unrecognized command: AT+CSRSF=1,1,1,1,1,7
< Jan  5 03:51:31 jon-laptop rtkit-daemon[1811]: Recovering from system lockup, not allowing further RT threads.
< Jan  4 19:51:31  rtkit-daemon[1811]: last message repeated 4 times
< Jan  4 19:51:31 jon-laptop bluetoothd[1143]: Operation not supported (95)
< Jan  4 19:51:31 jon-laptop bluetoothd[1143]: headset_resume_complete: resume failed
< Jan  4 19:51:31 jon-laptop pulseaudio[1807]: [bluetooth] module-bluetooth-device.c: Received error condition: Input/output error
< Jan  4 19:51:32 jon-laptop kernel: [  493.644150] input: 00:18:16:38:F1:4D as /devices/virtual/input/input14
```
headphones NOT LISTED in pavucontrol.

syslog after plugging in USB bt (0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode))
```
jschall@jon-laptop:~$ diff /var/log/syslog ~/syslog
5335,5342d5334
< Jan  4 19:56:12 jon-laptop kernel: [  772.887505] usb 2-1.1: new full speed USB device number 9 using ehci_hcd
< Jan  4 19:56:12 jon-laptop bluetoothd[1143]: HCI dev 0 registered
< Jan  4 19:56:12 jon-laptop bluetoothd[1143]: Listening for HCI events on hci0
< Jan  4 19:56:12 jon-laptop bluetoothd[1143]: HCI dev 0 up
< Jan  4 19:56:12 jon-laptop bluetoothd[1143]: input-headset driver probe failed for device 20:13:E0:68:08:BA
< Jan  4 19:56:12 jon-laptop bluetoothd[1143]: Adapter /org/bluez/1143/hci0 has been enabled
< Jan  4 19:56:12 jon-laptop pulseaudio[1807]: [pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod
< Jan  4 19:57:13  pulseaudio[1807]: last message repeated 2 times
```

syslog after connecting headphones to USB bt
```
jschall@jon-laptop:~$ diff /var/log/syslog ~/syslog
5350,5353d5349
< Jan  4 19:59:29 jon-laptop bluetoothd[1143]: Badly formated or unrecognized command: AT+CSRSF=1,1,1,1,1,7
< Jan  5 03:59:31 jon-laptop rtkit-daemon[1811]: Successfully made thread 3676 of process 1807 (n/a) owned by '1000' RT at priority 5.
< Jan  5 03:59:31 jon-laptop rtkit-daemon[1811]: Supervising 1 threads of 1 processes of 1 users.
< Jan  4 19:59:31 jon-laptop kernel: [  971.786383] input: 00:18:16:38:F1:4D as /devices/virtual/input/input18
```
headphones LISTED in pavucontrol and functioning flawlessly.

Tested with a family member's identical Gazelle professional and got the same issue (so probably not hardware)

I can provide any additional info needed.

---

### Post by isantop on 2012-01-05
Actually, it is likely a hardware issue. While not necessarily a failure, my guess is that the headphones are not compatible with the 6230's bluetooth adapter. It's unlikely to be software, since it works fine on the external dongle.

What is the make and model of the headphones? I can try and look to see if any known issues like this exist.

---

### Post by jschall1 on 2012-01-05
> **isantop said:**
> Actually, it is likely a hardware issue. While not necessarily a failure, my guess is that the headphones are not compatible with the 6230's bluetooth adapter. It's unlikely to be software, since it works fine on the external dongle.

What is the make and model of the headphones? I can try and look to see if any known issues like this exist.

Rocketfish RF-MAB2

I can't send a file to or browse files on my android phone, either, but I can with my USB adapter. There must be a driver issue...

That's all I got to test with. I was going to buy a razer orochi, but now I'm figuring it won't work.

After connecting phone:
```
Jan  5 13:24:24 jon-laptop obex-data-server: sdp_extract_seqtype: Unexpected end of packet
Jan  5 13:24:25 jon-laptop bluetoothd[1143]: input-headset driver probe failed for device 20:13:E0:68:08:BA
Jan  5 13:24:25 jon-laptop obex-data-server: sdp_extract_seqtype: Unexpected end of packet
Jan  5 13:25:09  obex-data-server: last message repeated 44 times
```
After trying to browse files I just have even more of those "sdp_extract_seqtype: Unexpected end of packet" messages
```
< Jan  5 13:25:10 jon-laptop obex-data-server: sdp_extract_seqtype: Unexpected end of packet
< Jan  5 13:26:11  obex-data-server: last message repeated 60 times
< Jan  5 13:27:11  obex-data-server: last message repeated 65 times
< Jan  5 13:28:11  obex-data-server: last message repeated 60 times
< Jan  5 13:29:06  obex-data-server: last message repeated 56 times
```
After trying to send files:
```
< Jan  5 13:29:06 jon-laptop obex-client[10644]: obex-client daemon 0.42
< Jan  5 13:29:06 jon-laptop bluetoothd[1143]: Mode session 0x7f61f04ea5c0 with :1.181 activated
< Jan  5 13:29:07 jon-laptop obex-client[10644]: Connection refused (111)
< Jan  5 13:29:07 jon-laptop obex-data-server: sdp_extract_seqtype: Unexpected end of packet
```

---

### Post by isantop on 2012-01-05
About the issue with your phone, there is a bug in Ubuntu's bluetooth system that causes that error. If you retry a few times, you should be able to transfer files.

For the headphones, are they pairing with the laptop at all?

---

### Post by jschall1 on 2012-01-05
> **isantop said:**
> About the issue with your phone, there is a bug in Ubuntu's bluetooth system that causes that error. If you retry a few times, you should be able to transfer files.

For the headphones, are they pairing with the laptop at all?

I've retried plenty of times, and it doesn't work until I plug in a different adapter. Then it works. Every. Single. Time. (that I've tried it, anyway.)

The headphones are indeed pairing with the laptop. The headphones beep like they're connected and kdebluetooth says they're connected. I just don't get any audio. Again, no problem with $2 USB bt adapter.

---

### Post by jschall1 on 2012-01-05
Is there an alternative wifi+bt card that does bluetooth better? My mom's gazp6 had the default realtek card originally but it had serious wifi problems on the university campus where she teaches and I go to school, so we swapped it for the advanced-n. I don't think I'd want to risk buying one of those again.

---

### Post by jschall1 on 2012-01-05
YAY I FIXED IT!!!!!!!!!
options btusb reset=1
Headphones working, need to test phone now.

---

### Post by jschall1 on 2012-01-05
Still no bueno on sending a file to the phone. While I really don't care about that because I can just use USB, I'd still love to get it to work.

---

### Post by isantop on 2012-01-06
How are you sending the file, and how are you retrying?

I find that I can get it to work if I send the File by right-clicking on it and choosing "Send to..." Select The bluetooth option and the phone, then check the box to send it packed in a .zip file (As this helps ensure the android device will accept the file).

Then, click send. If it fails, click retry in the dialog, and you may need to click it quickly. Keep trying this, and it should eventually go through.

---

### Post by jschall1 on 2012-01-23
An update to this issue - after reinstalling kubuntu, and reapplying the option btusb reset=1 fix, it didn't work. I removed the option and forgot about it for a while.

I've been having problems with bluetooth disappearing on resume from sleep, so I just starting screwing with bluetooth. While I was doing so, I tried connecting the headset several times, and eventually it connected. I haven't changed any configuration at all, but now it works every time again, like it did before. Very weird.

---

### Post by runny6play on 2012-01-25
Its worth mentioning that androids dont have native bluetooth send and recive... you need this app [https://market.android.com/details?id=it.medieval.blueftp](https://market.android.com/details?id=it.medieval.blueftp)

I could be wrong for some phones but a lot dont

---

### Post by jschall1 on 2012-01-26
> **runny6play said:**
> Its worth mentioning that androids dont have native bluetooth send and recive... you need this app [https://market.android.com/details?id=it.medieval.blueftp](https://market.android.com/details?id=it.medieval.blueftp)

I could be wrong for some phones but a lot dont

That would be a good explanation.
I have since bought my Razer Orochi (which I LOVE), and attached a bluetooth adapter to my printer. They both work great.

---

### Post by jschall1 on 2012-01-26
By the way, I had been having issues with my bluetooth icon disappearing on suspend/resume. I fixed that by adding a file to /etc/pm/sleep.d/ that runs /etc/init.d/bluetooth stop/start on sleep/resume.

The issue seemed to be exclusive to KDE.

---


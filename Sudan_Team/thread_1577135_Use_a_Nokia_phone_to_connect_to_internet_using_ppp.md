---
title: "Use a Nokia phone to connect to internet using pppconfig"
date: 2010-09-18
forum: Sudan Team
---

### Post by zero-n on 2010-09-18
Before we start connecting to Internet using your phone is not a good way cause it is costly so be **[COLOR=Red]AWARE[/COLOR]** of what you are doing.



I am running [COLOR=DarkOrange]**Ubuntu 10.04 LTS**[/COLOR] & using [[COLOR=Red]**N73**[/COLOR]]("http://en.wikipedia.org/wiki/Nokia_N73") Nokia phone connected with DKU-50 cable. & pppconfig is installed be default so there is no need to install it.


1- Connect your phone & when prompt select [COLOR=Red]**PC Suite**[/COLOR] Mode so your phone can be recognized as a modem.

2- Open terminal and run this command
```

sudo dmesg | tail

```the output should be something like this:
```

[ 6274.113214] usb 4-2: configuration #1 chosen from 1 choice
[ 6274.127179] cdc_acm 4-2:1.8: ttyACM0: USB ACM device
[ 6274.133111] usb 4-2: bad CDC descriptors
[ 6274.143475] usb 4-2: bad CDC descriptors
[ 6358.144057] usb 4-2: USB disconnect, address 5
[ 6363.572030] usb 4-2: new full speed USB device using uhci_hcd and address 6
[ 6363.744998] usb 4-2: configuration #1 chosen from 1 choice
[ 6363.758924] cdc_acm 4-2:1.8:**[COLOR=Red] ttyACM0[/COLOR]**: USB ACM device
[ 6363.764907] usb 4-2: bad CDC descriptors
[ 6363.772421] usb 4-2: bad CDC descriptors

```what is important here is **[COLOR=Red]tty[/COLOR]ACM0** (my phone modem) form the command output remember your ttyXXX cause you will need it.

3- From terminal run this command
```

sudo pppconfig

```4- Select [COLOR=Red]**Create a connection**[/COLOR].

5- Enter your Internet provider name or any name you like. remember you will need this name to make the connection. I will call it isp.

6- Use your DNS server type mine is **[COLOR=Red]Dynamic[/COLOR]**.

7- Select [COLOR=Red]**PAP**[/COLOR] authentication method.

8- Enter you username. You can't leave this field empty.

9- Enter your password. You can't leave this field empty.

10- Enter you port speed. If you are not sure just accept the default.

11- Select method of dialing as [COLOR=Red]**Tone**[/COLOR].

12 - Enter phone number.

13- You can select yes to detect modem automatically or no to specify it by you self i will choose no & i will use the name form step2 preceded with /dev
```

/dev/ttyACM0

```14 - Select[COLOR=Red]** Finished write file & return to main menu**[/COLOR]. Configuration file will be in[COLOR=Blue] **/etc/ppp/peers/CONNECTION_NAME_AT_STEP_2**[/COLOR].

15- Quit the tool





_**Connect & Disconnect:**_

1- connect:
```

sudo pon [COLOR=Red]**CONNECTION_NAME_AT_STEP_2**[/COLOR]

```2- disconnect:
```

sudo poff [COLOR=Red]**CONNECTION_NAME_AT_STEP_2**[/COLOR]

```change [COLOR=Red]**CONNECTION_NAME_AT_STEP_2 **[/COLOR]with your specified name


If you want to change something you can edit [COLOR=Blue]**/etc/ppp/peers/CONNECTION_NAME_AT_STEP_2 **[/COLOR]

**credit goes [here]("http://atunu.blogspot.com/2008/02/linux-redux-use-your-gprs-phone-as.html")**

---


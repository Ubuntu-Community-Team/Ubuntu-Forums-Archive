---
title: "pam_usb &amp; screensaver"
date: 2007-04-18
forum: Server Platforms
---

### Post by aamukahvi on 2007-04-18
(Yes I have read the sticky, but this has to do with security and maybe servers, too, if you as a server admin just want some convenience... :P feel free to move this if you feel there's a more appropriate forum for it)

Hi,

I read about a guy on the Gutsy forum who used pam_usb to allow passwordless login. That sounded great so naturally I had to try. Fetched the source.tgz from sourceforge, compiled, checkinstalled.

It works for gdm (I can login without password when the USBkey is attached), but I can't make it lock the session with gnome-screensaver when I remove the key. Is there anyone here who could help me with this?

Also sudo works without providing password, which is ***not*** what I want. I tried disabling it but it doesn't seem to work...

Here's /etc/pamusb.conf:
```
<?xml version="1.0" ?>
<configuration>
	<!-- Default options -->
	<defaults>
		<!-- Example:
			<option name="debug">true</option>
		-->
	</defaults>

	<!-- Device settings -->
	<devices>
	<device id="CruzerMini">
	<vendor>
		SanDisk Corporation
	</vendor>
	<model>
		Cruzer Mini
	</model>
	<serial>
		SNDK*[censored]*
	</serial>
	<volume_uuid>
		5C10-94F7
	</volume_uuid>
</device></devices>


	<!-- User settings -->
	<users>
			<user id="toni">
				<device>CruzerMini</device>
				<option name="quiet">true</option>
				<agent event="lock">gnome-screensaver-command -lock</agent>
				<agent event="unlock">gnome-screensaver-command -deactivate</agent>
			</user>
	</users>

	<!-- Services settings (e.g. gdm, su, sudo...) -->
	<services>
		<!-- Example: Speed up hotplugging by disabling one time pads -->
		<service id="pamusb-agent">
			<option name="one_time_pad">false</option>
		</service>
		<service id="sudo">
			<option name="enable">false</option>
		</service>
	</services>
</configuration>
```

---

### Post by hanjet on 2007-09-01
> **aamukahvi said:**
> 
Also sudo works without providing password, which is ***not*** what I want. I tried disabling it but it doesn't seem to work...


Can't really help you with the screensaver problem, since it worked right away for me (xscreensaver on xubuntu 7.04).

I had the same issue as you with the sudo though, and to disable sudo authentication with the USB dongle, and enable all other authentications, you simply have to edit **/etc/pam.d/sudo** so it does not use common-auth (which uses pam_usb). Basically, you make it ask for your password (just like before).

This is what **sudo** should look like:

```
#%PAM-1.0

auth    required        pam_unix.so nullok_secure 
```

Hope this helps, and good luck with your other issue.

---


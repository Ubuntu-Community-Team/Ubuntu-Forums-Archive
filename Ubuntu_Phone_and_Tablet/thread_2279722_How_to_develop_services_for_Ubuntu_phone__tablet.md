---
title: "How to develop services for Ubuntu phone / tablet?"
date: 2015-05-25
forum: Ubuntu Phone and Tablet
---

### Post by CaesarS on 2015-05-25
Hello,

Application focus seem to be on foreground apps with UI, at least from what I've gleaned on the web pages (HTML, Qt, etc.).

Is there a way to develop background services? Where the UI makes use of the service.

Is it possible and how would a background service be coded?

Many Thanks, Caesar.

---

### Post by ian-weisser on 2015-05-25
Ideally, your UI should be in small UI-specific apps, and all your real heavy lifting logic and core functions should be in a headless background service.

Background services can be written in any language. They can be written in a different language than the UI process (the current favorite UI language is QML).

Background services communicate with UI processes using dbus. dbus is  the generally-accepted public (and discoverable) way to expose a service  API. dbus bindings exist for most languages.

Your background services should usually run as root...unless your service has a network connection or other security issue. Then your service should run as a separate system user (not you, not root).

Always-on daemons generally start at boot (using an Upstart .conf file or systemd .service file), and supervised and respawned by init (if needed).
On-demand services are generally started by dbus when called (using a dbus .service file).

You can listen to dbus using the d-feet package, among others.
One good example of an always-on service with multiple clients and a public API is evolution-data-server. Another is Network Manager.



EXAMPLE UI CLIENT
Runs as user
Starts when user clicks on it
Written in favorite UI language
Communicates with service using dbus or pipes or sockets
Communicates with other services using dbus

EXAMPLE BACKGROUND SERVICE
Runs as root
Totally headless - output to logfiles. Console output only for debugging.
Written in any language you like
Communicates with your client using dbus or pipes or sockets
Communicates with other system and user services (Network Manager, Geolocation, Calendar, Contacts, Power Manager, etc) using dbus 
dbus API means other clients and services can query your service
Started by dbus upon first request from a client or another service

---

### Post by CaesarS on 2015-05-26
Thank you Ian! Specifically, can I write it using Java? (is there a Java runtime equivalent to say OpenJDK?)

---


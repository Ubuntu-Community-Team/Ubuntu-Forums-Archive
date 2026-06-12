---
title: "Anyone have expierence troubleshooting Docker containers?"
date: 2018-12-30
forum: Virtualisation
---

### Post by dev18 on 2018-12-30
Greetings,
    I have a Ubuntu 18.04 VPS that I'm trying to learn Docker on. Currently, I just have an OpenVPN AS container running. (It doesn't run or use the web UI to my knowledge.) Now, I'm trying to run a ZoneMinder container for my security IP cameras. I've done:

[I]docker pull kylejohnson/zoneminder
docker run -p 80:80 --name=zoneminder -d kylejohnson/zoneminder[/I]

    The container starts without error, but the web server is not reachable. When I check the processes, it appears to be exiting without error. I'm not really sure what the next course of action would be to getting it to work. I've tried running it on different ports like "-p 60:80" and stopping Apache2 on the Ubuntu server.

[I]root@vpn01:~# docker run -p 80:80 --name=zoneminder -d kylejohnson/zoneminder
7e8b3f719e37992abb0396451112777e6e25ff5cbd5d6ecd4242d98fd4e75adb
root@vpn01:~#
root@vpn01:~# docker ps -a
CONTAINER ID        IMAGE                    COMMAND                  CREATED             STATUS                     PORTS                    NAMES
7e8b3f719e37        kylejohnson/zoneminder   "/bin/sh -c '/ZoneMi&#8230;"   15 seconds ago      Exited (0) 3 seconds ago                            zoneminder
36ed45d73727        kylemanna/openvpn        "ovpn_run"               4 days ago          Up 4 days                  0.0.0.0:1194->1194/udp   serene_wright
a9cacf26f72b        kylemanna/openvpn        "ovpn_run"               4 days ago          Exited (0) 4 days ago                               priceless_almeida
2c37f38b0ae2        linuxserver/openvpn-as   "/init"                  5 days ago          Exited (0) 4 days ago                               openvpn-as[/I]

---


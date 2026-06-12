---
title: "USB MIDI Keyboard keeps connecting and disconnecting on JACK"
date: 2013-07-18
forum: Ubuntu Studio
---

### Post by rohtsiu on 2013-07-18
Hello there! Just started trying out Ubuntu Studio but this issue of connecting my Casio CTK-3000 keyboard is driving me nuts.

It has USB MIDI, and I checked to make sure that it works fine on my Windows PC using Anvil Studio, all the MIDI commands being detected consistently, even the pitch bend wheel.

But on Ubuntu Studio, it shows up as CASIO USB-MIDI and then disappears and reappears, over and over. If I run amidi -l -a one moment it will show "Dir Device    NameIO  hw:1,0,0  CASIO USB-MIDI MIDI 1"
and the next it will be empty, with a seemingly random frequency of around 0.5 - 2 Hz. On the qjackctl connections window it just flashes randomly "20:CASIO USB-MIDI" and here is and example of what it says under Messages:

22:53:13.549 ALSA connection change.
22:53:13.854 ALSA connection graph change.
22:53:13.864 JACK connection graph change.
22:53:13.954 JACK connection change.
22:53:13.956 ALSA connection change.
22:53:13.974 ALSA connection graph change.
22:53:13.987 JACK connection graph change.
Thu Jul 18 22:53:13 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:13 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:13 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:13 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:13 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:13 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:13 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:13 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:14.159 JACK connection change.
22:53:14.161 ALSA connection change.
22:53:15.560 ALSA connection graph change.
22:53:15.568 ALSA connection change.
22:53:15.569 JACK connection graph change.
22:53:15.574 ALSA connection graph change.
22:53:15.772 ALSA connection change.
Thu Jul 18 22:53:15 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:15 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:15 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:15 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:16.101 ALSA connection graph change.
22:53:16.108 JACK connection graph change.
22:53:16.177 JACK connection change.
22:53:16.180 ALSA connection change.
22:53:16.226 ALSA connection graph change.
22:53:16.235 JACK connection graph change.
22:53:16.383 JACK connection change.
22:53:16.385 ALSA connection change.
22:53:16.604 ALSA connection graph change.
22:53:16.609 JACK connection graph change.
Thu Jul 18 22:53:16 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:16 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:16 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:16 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:16 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:16 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:16 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:16 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:17.108 JACK connection graph change.
22:53:17.110 ALSA connection graph change.
22:53:17.194 JACK connection change.
22:53:17.196 ALSA connection change.
22:53:17.223 ALSA connection graph change.
22:53:17.234 JACK connection graph change.
22:53:17.399 JACK connection change.
22:53:17.402 ALSA connection change.
22:53:17.608 JACK connection graph change.
22:53:17.609 ALSA connection graph change.
22:53:17.611 JACK connection change.
22:53:17.612 ALSA connection change.
22:53:17.613 JACK connection graph change.
22:53:17.618 ALSA connection graph change.
22:53:17.816 JACK connection change.
22:53:17.818 ALSA connection change.
Thu Jul 18 22:53:17 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:17 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:17 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:17 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:17 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:17 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:17 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:17 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:18.717 ALSA connection graph change.
Cannot read socket fd = 23 err = Success
Cannot read socket fd = 23 err = Success
Cannot read socket fd = 23 err = Success
Cannot read socket fd = 23 err = Success
Connect: can't connect named semaphore name = jack_sem.1000_default_	 err = Permission denied
Cannot read socket fd = 23 err = Permission denied
Cannot read socket fd = 23 err = Permission denied
Cannot read socket fd = 23 err = Permission denied
Cannot read socket fd = 23 err = Permission denied
Cannot read socket fd = 23 err = Permission denied
22:53:18.826 ALSA connection change.
22:53:18.974 ALSA connection graph change.
22:53:18.991 JACK connection graph change.
22:53:19.030 ALSA connection change.
Thu Jul 18 22:53:18 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:18 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:18 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:19 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:19.359 ALSA connection graph change.
22:53:19.367 JACK connection graph change.
22:53:19.437 JACK connection change.
22:53:19.438 ALSA connection change.
22:53:19.474 ALSA connection graph change.
22:53:19.488 JACK connection graph change.
22:53:19.642 JACK connection change.
22:53:19.645 ALSA connection change.
22:53:19.859 JACK connection graph change.
22:53:19.860 ALSA connection graph change.
Thu Jul 18 22:53:19 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:19 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:19 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:19 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:19 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:19 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:19 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:19 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:20.820 ALSA connection graph change.
22:53:20.828 JACK connection graph change.
22:53:20.866 JACK connection change.
22:53:20.868 ALSA connection change.
22:53:20.976 ALSA connection graph change.
22:53:20.988 JACK connection graph change.
Thu Jul 18 22:53:20 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:20 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:20 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:20 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:21.076 JACK connection change.
22:53:21.079 ALSA connection change.
22:53:21.353 ALSA connection graph change.
22:53:21.360 JACK connection graph change.
22:53:21.487 JACK connection graph change.
22:53:21.858 ALSA connection graph change.
22:53:21.860 JACK connection graph change.
22:53:21.891 JACK connection change.
22:53:21.893 ALSA connection change.
22:53:21.974 ALSA connection graph change.
22:53:21.986 JACK connection graph change.
Thu Jul 18 22:53:21 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:21 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:21 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:21 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:21 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:21 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:21 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:21 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:22.096 JACK connection change.
22:53:22.098 ALSA connection change.
22:53:22.353 ALSA connection graph change.
22:53:22.359 JACK connection graph change.
22:53:22.854 ALSA connection graph change.
22:53:22.864 JACK connection graph change.
22:53:22.908 JACK connection change.
22:53:22.909 ALSA connection change.
22:53:22.981 ALSA connection graph change.
22:53:22.987 JACK connection graph change.
Thu Jul 18 22:53:22 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:22 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:22 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:22 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:22 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:22 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:22 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:22 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:23.112 JACK connection change.
22:53:23.114 ALSA connection change.
22:53:24.613 JACK connection graph change.
22:53:24.615 ALSA connection graph change.
22:53:24.723 JACK connection change.
22:53:24.732 JACK connection graph change.
22:53:24.736 ALSA connection graph change.
22:53:24.935 JACK connection change.
Thu Jul 18 22:53:24 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:24 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:24 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:24 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:25.103 ALSA connection graph change.
22:53:25.113 JACK connection graph change.
22:53:25.140 JACK connection change.
22:53:25.141 ALSA connection change.
22:53:25.223 ALSA connection graph change.
22:53:25.234 JACK connection graph change.
22:53:25.347 JACK connection change.
22:53:25.350 ALSA connection change.
22:53:25.602 ALSA connection graph change.
22:53:25.610 JACK connection graph change.
Thu Jul 18 22:53:25 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:25 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:25 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:25 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:25 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:25 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:25 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:25 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:26.464 ALSA connection graph change.
22:53:26.473 JACK connection graph change.
22:53:26.562 JACK connection change.
22:53:26.565 ALSA connection change.
22:53:26.730 ALSA connection graph change.
22:53:26.739 JACK connection graph change.
22:53:26.768 JACK connection change.
22:53:26.770 ALSA connection change.
Thu Jul 18 22:53:26 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:26 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:26 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:26 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:27.706 ALSA connection graph change.
22:53:27.708 JACK connection graph change.
Thu Jul 18 22:53:27 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:27 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:27 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:27 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:28.107 ALSA connection graph change.
22:53:28.109 JACK connection graph change.
22:53:28.180 JACK connection change.
22:53:28.181 ALSA connection change.
22:53:28.233 JACK connection graph change.
22:53:28.235 ALSA connection graph change.
22:53:28.384 JACK connection change.
22:53:28.385 ALSA connection change.
22:53:28.602 ALSA connection graph change.
22:53:28.609 JACK connection graph change.
Thu Jul 18 22:53:28 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:28 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:28 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:28 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:28 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:28 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:28 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:28 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:29.472 ALSA connection graph change.
22:53:29.476 JACK connection graph change.
Thu Jul 18 22:53:29 2013: [1m[31mERROR: can't subscribe to 20:0 - Invalid argument[0m
Thu Jul 18 22:53:29 2013: port deleted: USB-Device-0x7cf:0x6803:midi/playback_1
Thu Jul 18 22:53:29 2013: port deleted: :midi/capture_1
22:53:30.379 ALSA connection graph change.
22:53:30.390 JACK connection graph change.
22:53:30.398 JACK connection change.
22:53:30.399 ALSA connection change.
22:53:30.473 ALSA connection graph change.
22:53:30.483 JACK connection graph change.
22:53:30.604 JACK connection change.
22:53:30.605 ALSA connection change.
22:53:30.854 ALSA connection graph change.
22:53:30.860 JACK connection graph change.
Thu Jul 18 22:53:30 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:30 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:30 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:30 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:30 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:30 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:30 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:30 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:31.354 ALSA connection graph change.
22:53:31.361 JACK connection graph change.
22:53:31.412 JACK connection change.
22:53:31.413 ALSA connection change.
22:53:31.481 ALSA connection graph change.
22:53:31.496 JACK connection graph change.
22:53:31.616 JACK connection change.
22:53:31.619 ALSA connection change.
Thu Jul 18 22:53:31 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:31 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:31 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:31 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:32.383 ALSA connection graph change.
22:53:32.390 JACK connection graph change.
22:53:32.429 JACK connection change.
22:53:32.430 ALSA connection change.
22:53:32.476 ALSA connection graph change.
22:53:32.482 JACK connection graph change.
22:53:32.633 JACK connection change.
22:53:32.636 ALSA connection change.
22:53:32.851 ALSA connection graph change.
22:53:32.858 JACK connection graph change.
Thu Jul 18 22:53:32 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:32 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:32 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:32 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:32 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:32 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:32 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:32 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:33.354 ALSA connection graph change.
22:53:33.364 JACK connection graph change.
22:53:33.446 JACK connection change.
22:53:33.447 ALSA connection change.
22:53:33.474 ALSA connection graph change.
22:53:33.489 JACK connection graph change.
22:53:33.651 JACK connection change.
22:53:33.654 ALSA connection change.
22:53:33.850 ALSA connection graph change.
22:53:33.860 JACK connection change.
22:53:33.861 ALSA connection change.
22:53:33.862 JACK connection graph change.
22:53:33.871 ALSA connection graph change.
Thu Jul 18 22:53:33 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:33 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:33 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:33 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:33 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:33 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:33 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:33 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:34.066 JACK connection change.
22:53:34.068 ALSA connection change.
22:53:35.102 ALSA connection graph change.
22:53:35.115 JACK connection graph change.
Cannot read socket fd = 23 err = Permission denied
Cannot read socket fd = 23 err = Permission denied
Cannot read socket fd = 23 err = Permission denied
Cannot read socket fd = 23 err = Permission denied
Cannot read socket fd = 23 err = Permission denied
22:53:35.604 ALSA connection graph change.
22:53:35.613 JACK connection graph change.
22:53:35.679 JACK connection change.
22:53:35.680 ALSA connection change.
22:53:35.723 ALSA connection graph change.
22:53:35.734 JACK connection graph change.
22:53:35.890 JACK connection change.
22:53:35.893 ALSA connection change.
Thu Jul 18 22:53:35 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:35 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:35 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:35 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:35 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:35 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:35 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:35 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:36.316 ALSA connection graph change.
22:53:36.326 JACK connection graph change.
22:53:36.853 ALSA connection graph change.
22:53:36.860 JACK connection graph change.
22:53:36.901 JACK connection change.
22:53:36.903 ALSA connection change.
22:53:36.973 ALSA connection graph change.
22:53:36.990 JACK connection graph change.
Thu Jul 18 22:53:36 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:36 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:36 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:36 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:36 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:36 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:36 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:36 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:37.106 JACK connection change.
22:53:37.109 ALSA connection change.
22:53:37.356 ALSA connection graph change.
22:53:37.362 JACK connection graph change.
22:53:37.852 ALSA connection graph change.
22:53:37.859 JACK connection graph change.
22:53:37.919 JACK connection change.
22:53:37.920 ALSA connection change.
22:53:37.985 JACK connection graph change.
22:53:37.988 ALSA connection graph change.
Thu Jul 18 22:53:37 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:37 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:37 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:37 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:37 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:37 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:37 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:37 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:38.123 JACK connection change.
22:53:38.125 ALSA connection change.
22:53:38.881 ALSA connection graph change.
22:53:38.894 JACK connection graph change.
22:53:38.931 JACK connection change.
22:53:38.932 ALSA connection change.
22:53:38.973 ALSA connection graph change.
22:53:38.989 JACK connection graph change.
Thu Jul 18 22:53:38 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:38 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:38 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:38 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:39.136 JACK connection change.
22:53:39.138 ALSA connection change.
22:53:40.347 ALSA connection graph change.
22:53:40.359 JACK connection graph change.
Thu Jul 18 22:53:40 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:40 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:40 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:40 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:41.379 ALSA connection graph change.
22:53:41.392 JACK connection graph change.
Thu Jul 18 22:53:41 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:41 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:41 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:41 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:42.078 JACK connection graph change.
22:53:42.081 ALSA connection graph change.
22:53:42.156 JACK connection change.
22:53:42.157 ALSA connection change.
22:53:42.229 ALSA connection graph change.
22:53:42.234 JACK connection graph change.
22:53:42.360 JACK connection change.
22:53:42.363 ALSA connection change.
22:53:42.602 ALSA connection graph change.
22:53:42.609 JACK connection graph change.
Thu Jul 18 22:53:42 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:42 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:42 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:42 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:42 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:42 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:42 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:42 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:45.424 ALSA connection graph change.
22:53:45.429 JACK connection graph change.
22:53:45.853 ALSA connection graph change.
22:53:45.859 JACK connection graph change.
22:53:45.989 JACK connection graph change.
Thu Jul 18 22:53:45 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:45 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:45 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:45 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:45 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:45 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:45 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:45 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:46.712 ALSA connection graph change.
22:53:46.718 JACK connection graph change.
22:53:46.793 JACK connection change.
22:53:46.794 ALSA connection change.
22:53:46.974 ALSA connection graph change.
22:53:46.988 JACK connection graph change.
22:53:46.998 JACK connection change.
22:53:46.999 ALSA connection change.
Thu Jul 18 22:53:46 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:46 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:46 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:46 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:47.355 ALSA connection graph change.
22:53:47.368 JACK connection graph change.
22:53:47.404 JACK connection change.
22:53:47.407 ALSA connection change.
22:53:47.481 ALSA connection graph change.
22:53:47.494 JACK connection graph change.
22:53:47.611 JACK connection change.
22:53:47.614 ALSA connection change.
Thu Jul 18 22:53:47 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:47 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:47 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:47 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:49.055 ALSA connection graph change.
22:53:49.062 JACK connection graph change.
22:53:49.222 JACK connection change.
22:53:49.233 ALSA connection graph change.
22:53:49.236 JACK connection graph change.
22:53:49.429 JACK connection change.
22:53:49.604 ALSA connection graph change.
22:53:49.612 JACK connection graph change.
22:53:49.633 JACK connection change.
22:53:49.634 ALSA connection change.
22:53:49.737 JACK connection graph change.
22:53:49.741 ALSA connection graph change.
22:53:49.837 JACK connection change.
22:53:49.839 ALSA connection change.
Thu Jul 18 22:53:49 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:49 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:49 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:49 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:49 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:49 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:49 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:49 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:50.485 ALSA connection graph change.
22:53:50.489 JACK connection graph change.
22:53:50.665 JACK connection change.
22:53:50.666 ALSA connection change.
22:53:50.731 ALSA connection graph change.
22:53:50.735 JACK connection graph change.
22:53:50.869 JACK connection change.
22:53:50.870 ALSA connection change.
Thu Jul 18 22:53:50 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:50 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:50 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:50 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:51.719 ALSA connection graph change.
22:53:51.727 JACK connection graph change.
22:53:51.876 JACK connection change.
22:53:51.877 ALSA connection change.
22:53:51.975 ALSA connection graph change.
22:53:51.989 JACK connection graph change.
Thu Jul 18 22:53:51 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:51 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:51 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:51 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:52.080 JACK connection change.
22:53:52.082 ALSA connection change.
22:53:52.975 ALSA connection graph change.
22:53:52.977 JACK connection graph change.
Thu Jul 18 22:53:52 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:52 2013: port created: CASIO-USB-MIDI:midi/capture_1
22:53:53.089 JACK connection change.
22:53:53.090 ALSA connection change.
22:53:53.234 ALSA connection graph change.
22:53:53.238 JACK connection graph change.
22:53:53.293 JACK connection change.
22:53:53.295 ALSA connection change.
Thu Jul 18 22:53:53 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:53 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:54.431 ALSA connection graph change.
22:53:54.438 JACK connection graph change.
22:53:54.852 ALSA connection graph change.
22:53:54.860 JACK connection graph change.
22:53:54.904 JACK connection change.
22:53:54.905 ALSA connection change.
22:53:54.979 ALSA connection graph change.
22:53:54.994 JACK connection graph change.
Thu Jul 18 22:53:54 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:54 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:54 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:54 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:54 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:54 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:54 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:54 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:55.108 JACK connection change.
22:53:55.110 ALSA connection change.
22:53:55.352 ALSA connection graph change.
22:53:55.358 JACK connection graph change.
22:53:55.852 ALSA connection graph change.
22:53:55.862 JACK connection graph change.
22:53:55.920 JACK connection change.
22:53:55.923 ALSA connection change.
22:53:55.991 JACK connection graph change.
22:53:55.998 ALSA connection graph change.
Thu Jul 18 22:53:55 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:55 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:55 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:55 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:55 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:55 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:55 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:55 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:56.126 JACK connection change.
22:53:56.128 ALSA connection change.
22:53:56.739 ALSA connection graph change.
22:53:56.746 JACK connection graph change.
22:53:56.935 JACK connection change.
22:53:56.938 ALSA connection change.
22:53:56.973 ALSA connection graph change.
22:53:56.989 JACK connection graph change.
Thu Jul 18 22:53:56 2013: port created: CASIO-USB-MIDI:midi/playback_1
Thu Jul 18 22:53:56 2013: port created: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:56 2013: port deleted: CASIO-USB-MIDI:midi/capture_1
Thu Jul 18 22:53:56 2013: port deleted: CASIO-USB-MIDI:midi/playback_1
22:53:57.141 JACK connection change.
22:53:57.144 ALSA connection change.
22:53:57.360 JACK connection graph change.
22:53:57.361 ALSA connection graph change.


Soooooo weird!! Does anybody know what's going on?

I tried killing pulseaudio, restarting the computer numerous times, manually making a connection using aconnect, using another USB cable (and as mentioned above using the same keyboard on another Windows PC works fine so I don't think it's the hardware) and have gotten nowhere. Everything else is working fine and I have tried connecting the Virtual MIDI Keyboard to Qsynth and it was pretty cool, just need to get my Casio keyboard connected properly. Some insight would really be appreciated!

Thanks.

---

### Post by rohtsiu on 2013-07-18
Oh and it appears that if I leave it to run for several minutes, it ends up at a not detected state. Unplugging and replugging in the USB cable restarts the process.

---

### Post by jejeman on 2013-07-19
Maybe it looses power, try diffrent USB port.
Maybe it isn't supported well by ALSA.
See, what happends in
```
lsusb
```
and
```
dmesg | tail -n 50
```
This looks like hardware/ALSA issue, not sound server one.

---

### Post by rohtsiu on 2013-07-19
Thanks. I tried all the USB ports and there doesn't seem to be any difference. Here are the results of the commands:

lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
dmesg | tail -n 50
```
[ 8686.694255] usb 4-1: new full-speed USB device number 78 using uhci_hcd
[ 8687.000077] hub 4-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[ 8687.000084] usb 4-1: USB disconnect, device number 78
[ 8687.207102] usb 4-1: new full-speed USB device number 79 using uhci_hcd
[ 8687.723154] usb 4-1: device not accepting address 79, error -71
[ 8687.825159] usb 4-1: new full-speed USB device number 80 using uhci_hcd
[ 8688.250155] hub 4-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[ 8688.250169] usb 4-1: USB disconnect, device number 80
[ 8688.459112] usb 4-1: new full-speed USB device number 81 using uhci_hcd
[ 8689.250105] hub 4-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[ 8689.250122] usb 4-1: USB disconnect, device number 81
[ 8689.459156] usb 4-1: new full-speed USB device number 82 using uhci_hcd
[ 8689.973146] usb 4-1: device not accepting address 82, error -71
[ 8690.075041] usb 4-1: new full-speed USB device number 83 using uhci_hcd
[ 8691.250191] hub 4-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[ 8691.250205] usb 4-1: USB disconnect, device number 83
[ 8691.458102] usb 4-1: new full-speed USB device number 84 using uhci_hcd
[ 8692.000150] hub 4-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[ 8692.000164] usb 4-1: USB disconnect, device number 84
[ 8692.209074] usb 4-1: new full-speed USB device number 85 using uhci_hcd
[ 8692.341749] usb 4-1: device descriptor read/all, error -71
[ 8692.445173] usb 4-1: new full-speed USB device number 86 using uhci_hcd
[ 8692.557096] usb 4-1: device descriptor read/64, error -71
[ 8693.298158] urb status -75
[ 8693.500164] hub 4-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[ 8693.500177] usb 4-1: USB disconnect, device number 86
[ 8693.706098] usb 4-1: new full-speed USB device number 87 using uhci_hcd
[ 8693.818114] usb 4-1: device descriptor read/64, error -71
[ 8694.074574] usb 4-1: unable to read config index 0 descriptor/all
[ 8694.074587] usb 4-1: can't read configurations, error -71
[ 8694.178161] usb 4-1: new full-speed USB device number 88 using uhci_hcd
[ 8695.250152] hub 4-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[ 8695.250166] usb 4-1: USB disconnect, device number 88
[ 8695.457128] usb 4-1: new full-speed USB device number 89 using uhci_hcd
[ 8695.615346] usb 4-1: string descriptor 0 read error: -71
[ 8695.619338] usb 4-1: can't set config #1, error -71
[ 8695.619593] hub 4-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[ 8695.619602] usb 4-1: USB disconnect, device number 89
[ 8695.827105] usb 4-1: new full-speed USB device number 90 using uhci_hcd
[ 8695.939137] usb 4-1: device descriptor read/64, error -71
[ 8696.192671] usb 4-1: unable to read config index 0 descriptor/all
[ 8696.192684] usb 4-1: can't read configurations, error -71
[ 8696.296269] usb 4-1: new full-speed USB device number 91 using uhci_hcd
[ 8696.810132] usb 4-1: device not accepting address 91, error -71
[ 8696.912119] usb 4-1: new full-speed USB device number 92 using uhci_hcd
[ 8697.322044] usb 4-1: device not accepting address 92, error -71
[ 8697.424057] usb 4-1: new full-speed USB device number 93 using uhci_hcd
[ 8697.451231] usb 4-1: device descriptor read/8, error -71
[ 8697.573311] usb 4-1: device descriptor read/8, error -71
[ 8697.674086] hub 4-0:1.0: unable to enumerate USB device on port 1

```

---

### Post by rohtsiu on 2013-07-19
Wow it's working now without disconnecting. Just tried turning off and turning on the keyboard and it's still working fine. It would seem that running lsusb BEFORE running jack somehow makes the USB driver work permanently rather than keep disconnecting. Pretty strange.

Well, thanks. So anybody with a CTK-3000 and Ubuntu, there ya go!

---

### Post by jejeman on 2013-07-20
Lsusb does nothing. You'r problem is probably just temporary gone, or something elese changed in the meentime.

Do you have problems with other USB devices?

---


---
title: "enble ipv6 in snort"
date: 2011-08-23
forum: Security
---

### Post by lolek198787 on 2011-08-23
Hi,

How to enable ipv6 in snort. I read that it must compilate with --enable-ipv6 but still don't know how?

---

### Post by unspawn on 2011-08-25
> **lolek198787 said:**
> compilate with --enable-ipv6 but still don't know how?
D/L and decompress source tarball, use './compile --enable-ipv6 [any_other_options] && make && install' triplet.

---

### Post by lemming465 on 2011-08-25
To elaborate on unspawns suggestion, first download the source tarball.
Unpack it, e.g. "tar -xzf snort-2.9.0.5.tar.gz'.

I usually like to also download a ruleset, because the snort.conf file from the ruleset has a comment line showing what configuration options sourcefire is currently favoring.

This week, I'm using a paid subscription (VRT), in passive mode, so I drop all the active response options.  I keep the two key IPv6 options, namely "--enable-ipv6 --enable-gre".  The name of the latter is a little misleading; what it really does is activate tunnel decoding (1 layer worth) for GRE, PPP, and protocol 41 (used by IPv6 over IPv4 tunnel protocols 6in4 (with tunnel brokers), 6to4 (public anycast), 6rd (ISP near native), etc.  This results in a configuration step for me of```

cd snort-2.9.0.5

./configure  --enable-ipv6 --enable-gre --enable-mpls --enable-targetbased \
  --enable-decoder-preprocessor-rules --enable-ppm --enable-perfprofiling \
  --enable-zlib --enable-reload

make
sudo make install
```
This will put everything under /usr/local, which is a safe and reasonable choice.  Other options to ./configure, visible if you run "./configure --help", let you tune the locations and some other components if you need to.

You still have to do the usual snort setup stuff: massage the configuration file, point it at some rules, etc.  For IPv6 enabled snorts, which should really be all of them these days, be sure to use "ipvar" as the variable keyword, not the old "ip" in the configuration file.  Then mix and match IPv4 and IPv6 addresses and prefixes to your hearts content.

---


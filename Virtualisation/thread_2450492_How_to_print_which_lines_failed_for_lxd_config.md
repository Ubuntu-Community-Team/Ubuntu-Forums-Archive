---
title: "How to print which lines failed for lxd config?"
date: 2020-09-14
forum: Virtualisation
---

### Post by andrew102 on 2020-09-14
When creating a lxd --vm with option for configuration file --config, I get an error. This is a config I saved from a prior working machine, so I am trying to work out which line is causing it to fail. Running the create command with --debug does not provide any further clarity.

Error: Bad key=value pair: /path/to/config.yaml

How to make lxc print the failing key pair? Or is there also a separate config validator command that can be executed?

---


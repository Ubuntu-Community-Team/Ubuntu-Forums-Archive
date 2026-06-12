---
title: "Early Pipewire experiences. No audio and return of the suspended sound device"
date: 2022-05-19
forum: Ubuntu Development Version
---

### Post by Smask on 2022-05-19
So, we went from pulseaudio to pipewire. The system expected a pulseaudio device,but couldn't find any. Googling and found a Fedora discussion, mentioning wireplumber. Installed wireplumber, rebooted and I got sound back. But with annoying start pops. The system suspend the device when idling and that I fixed during pulseaudio era, but new configuration files...

---

### Post by #&amp;thj^% on 2022-05-19
```
cat /usr/share/wireplumber/main.lua.d/50-alsa-config.lua

alsa_monitor.properties = {
  -- Create a JACK device. This is not enabled by default because
  -- it requires that the PipeWire JACK replacement libraries are
  -- not used by the session manager, in order to be able to
  -- connect to the real JACK server.
  --["alsa.jack-device"] = false,

  -- Reserve devices via org.freedesktop.ReserveDevice1 on D-Bus
  ["alsa.reserve"] = true,
  --["alsa.reserve.priority"] = -20,
  --["alsa.reserve.application-name"] = "WirePlumber",

  -- Enables MIDI functionality
  ["alsa.midi"] = true,

  -- Enables monitoring of alsa MIDI devices
  ["alsa.midi.monitoring"] = true,
}

alsa_monitor.rules = {
  -- An array of matches/actions to evaluate.
  -- 
  -- If you want to disable some devices or nodes, you can apply properties per device as the following example.
  -- The name can be found by running pw-cli ls Device, or pw-cli dump Device
  --{
  --  matches = {
  --    {
  --      { "device.name", "matches", "name_of_some_disabled_card" },
  --    },
  --  },
  --  apply_properties = {
  --    ["device.disabled"] = true,
  --  },
  --}
  {
    -- Rules for matching a device or node. It is an array of
    -- properties that all need to match the regexp. If any of the
    -- matches work, the actions are executed for the object.
    matches = {
      {
        -- This matches all cards.
        { "device.name", "matches", "alsa_card.*" },
      },
    },
    -- Apply properties on the matched object.
    apply_properties = {
      -- Use ALSA-Card-Profile devices. They use UCM or the profile
      -- configuration to configure the device and mixer settings.
      ["api.alsa.use-acp"] = true,

      -- Use UCM instead of profile when available. Can be
      -- disabled to skip trying to use the UCM profile.
      --["api.alsa.use-ucm"] = true,

      -- Don't use the hardware mixer for volume control. It
      -- will only use software volume. The mixer is still used
      -- to mute unused paths based on the selected port.
      --["api.alsa.soft-mixer"] = false,

      -- Ignore decibel settings of the driver. Can be used to
      -- work around buggy drivers that report wrong values.
      --["api.alsa.ignore-dB"] = false,

      -- The profile set to use for the device. Usually this is
      -- "default.conf" but can be changed with a udev rule or here.
      --["device.profile-set"] = "profileset-name",

      -- The default active profile. Is by default set to "Off".
      --["device.profile"] = "default profile name",

      -- Automatically select the best profile. This is the
      -- highest priority available profile. This is disabled
      -- here and instead implemented in the session manager
      -- where it can save and load previous preferences.
      ["api.acp.auto-profile"] = false,

      -- Automatically switch to the highest priority available port.
      -- This is disabled here and implemented in the session manager instead.
      ["api.acp.auto-port"] = false,

      -- Other properties can be set here.
      --["device.nick"] = "My Device",
    },
  },
  {
    matches = {
      {
        -- Matches all sources.
        { "node.name", "matches", "alsa_input.*" },
      },
      {
        -- Matches all sinks.
        { "node.name", "matches", "alsa_output.*" },
      },
    },
    apply_properties = {
      --["node.nick"]              = "My Node",
      --["priority.driver"]        = 100,
      --["priority.session"]       = 100,
      --["node.pause-on-idle"]     = false,
      --["resample.quality"]       = 4,
      --["channelmix.normalize"]   = false,
      --["channelmix.mix-lfe"]     = false,
      --["audio.channels"]         = 2,
      --["audio.format"]           = "S16LE",
      --["audio.rate"]             = 44100,
      --["audio.allowed-rates"]    = "32000,96000"
      --["audio.position"]         = "FL,FR",
      --["api.alsa.period-size"]   = 1024,
      --["api.alsa.headroom"]      = 0,
      --["api.alsa.disable-mmap"]  = false,
      --["api.alsa.disable-batch"] = false,
      --["session.suspend-timeout-seconds"] = 5,  -- 0 disables suspend
    },
  },
}

```
The relevant configuration file is** /usr/share/wireplumber/main.lua.d/50-alsa-config.lua**, but don't edit the system version of it!

You need to copy it into** /etc/wireplumber/main.lua.d/ (global config)** or **~/.config/wireplumber/main.lua.d/ (user config)** and make the necessary changes.

The easiest way is to copy it into the *global config location so that it applies to all user accounts:

```
sudo cp -a /usr/share/wireplumber/main.lua.d/50-alsa-config.lua /etc/wireplumber/main.lua.d/50-alsa-config.lua
sudo nano /etc/wireplumber/main.lua.d/50-alsa-config.lua
```

You then need to scroll down to the bottom of the file, inside the **apply_properties section**, and add a line there which says:
```

["session.suspend-timeout-seconds"] = 0
```
I've done more with my setup, but nonrelevant in your post.
```
wpctl status
PipeWire 'pipewire-0' [0.3.51, me@arch-me, cookie:<sniped cookie>]
 &#9492;&#9472; Clients:
        31. WirePlumber                         [0.3.51, me@arch-me, pid:1105]
        32. xfce4-pulseaudio-plugin             [0.3.51, me@arch-me, pid:1073]
        33. pipewire-pulse                      [0.3.51, me@arch-me, pid:1106]
        35. WirePlumber [export]                [0.3.51, me@arch-me, pid:1105]
        69. Strawberry device finder            [0.3.51, me@arch-me, pid:18592]
        70. strawberry                          [0.3.51, me@arch-me, pid:18592]
        76. virt-manager                        [0.3.51, me@arch-me, pid:220184]
        77. virt-manager                        [0.3.51, me@arch-me, pid:220184]
        78. wpctl                               [0.3.51, me@arch-me, pid:245665]

Audio
 &#9500;&#9472; Devices:
 &#9474;      43. HDA NVidia                          [alsa]
 &#9474;      44. UOEOS Laptop Dock                   [alsa]
 &#9474;      45. Family 17h/19h HD Audio Controller  [alsa]
 &#9474;      63. SRS-XB22                            [bluez5]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;      52. UOEOS Laptop Dock Digital Stereo (IEC958) [vol: 0.74]
 &#9474;      54. Family 17h/19h HD Audio Controller Analog Stereo [vol: 0.74]
 &#9474;  *   64. SRS-XB22                            [vol: 0.60]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;      53. UOEOS Laptop Dock Digital Stereo (IEC958) [vol: 0.74]
 &#9474;  *   55. Family 17h/19h HD Audio Controller Analog Stereo [vol: 0.74]
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:
        71. strawberry                                                  
             73. output_FL       > SRS-XB22:playback_FL
             75. output_FR       > SRS-XB22:playback_FR

Video
 &#9500;&#9472; Devices:
 &#9474;      41. Integrated Camera                   [v4l2]
 &#9474;      42. Integrated Camera                   [v4l2]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   46. Integrated Camera                  
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Settings
 &#9492;&#9472; Default Configured Node Names:
         0. Audio/Sink    bluez_output.F8_DF_15_7F_64_73.a2dp-sink
         1. Audio/Source  alsa_input.pci-0000_05_00.6.analog-stereo


```
Dang it, forgot to mention this, WirePlumber has to be restarted in order for changes to take effect:

```
systemctl --user restart wireplumber
```

---

### Post by #&amp;thj^% on 2022-05-19
> **Smask said:**
>  But with annoying start pops. 
As for your poping, try this if it persist's
```
cd /usr/share/wireplumber/scripts/

``` 
open with a text editor as root:
```
me@me-Standard-PC-Q35-ICH9-2009:/usr/share/wireplumber/scripts$ sudoedit suspend-node.lua

```
don't woory I have backup for you if something goes astray.
Make it look as this:
```
-- WirePlumber
--
-- Copyright © 2021 Collabora Ltd.
--    @author George Kiagiadakis <george.kiagiadakis@collabora.com>
--
-- SPDX-License-Identifier: MIT

om = ObjectManager {
  Interest { type = "node",
    Constraint { "media.class", "matches", "Audio/*" }
  },
  Interest { type = "node",
    Constraint { "media.class", "matches", "Video/*" }
  },
}

sources = {}

om:connect("object-added", function (om, node)
  node:connect("state-changed", function (node, old_state, cur_state)
    -- Always clear the current source if any
    local id = node["bound-id"]
    if sources[id] then
      sources[id]:destroy()
      sources[id] = nil
    end

--    -- Add a timeout source if idle for at least 3 seconds
--    if cur_state == "idle" then
--      -- honor "session.suspend-timeout-seconds" if specified
--      local timeout =
--          tonumber(node.properties["session.suspend-timeout-seconds"]) or 3

--      if timeout == 0 then
--        return
--      end

--      -- add idle timeout; multiply by 1000, timeout_add() expects ms
--      sources[id] = Core.timeout_add(timeout * 1000, function()
--        -- Suspend the node
--        Log.info(node, "was idle for a while; suspending ...")
--        node:send_command("Suspend")

--        -- Unref the source
--        sources[id] = nil

--        -- false (== G_SOURCE_REMOVE) destroys the source so that this
--        -- function does not get fired again after 3 seconds
--        return false
--      end)
--    end

  end)
end)

om:activate()

```
again restart Wireplumber.
should have fixed your poping

---

### Post by Frogs Hair on 2022-05-20
There are some trouble-shooting options linked.

[https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/Troubleshooting#stuttering-audio-in-virtual-machine](https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/Troubleshooting#stuttering-audio-in-virtual-machine)

---


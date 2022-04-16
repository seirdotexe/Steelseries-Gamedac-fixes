<h1 align="center">Steelseries Gamedac fixes</h1>
<h3 align="center">Detailed instructions on how to fix your Steelseries Gamedac setup</h3>

![](https://i.ibb.co/gJ1nN33/a.png)

---

# The issue

The Gamedac suffers from bidirectional audio issues. Because of this, you can't hear certain sounds unless you're looking directly at them. This issue is persistent in a wide range of games, making them all unplayable. It seems to occur in Unreal Engine 3/4 games the most, but also custom engines like Remedy's Northlight engine are having issues. I suspect that the **6-channel** setup of the Gamedac driver is the issue, and there's no other way to fix this other than using third party software.

# The fix

The fix for this issue is to make use of a Virtual Audio Cable (VAC). You may have never heard of this software before, but it's super simple. To fix this breaking issue, we have to listen to the Gamedac's actual audio input driver over our VAC, emulating the incoming sound in a sense. The bonus for this is that we can also control our audio input source extensively.

Click [here](https://streamable.com/k34wpy) for an example with VAC and [here](https://streamable.com/etkqk6) for an example without VAC.

# The software

The [VAC](https://en.wikipedia.org/wiki/Virtual_Audio_Cable) from Eugene Muzychenko is currently the best working software as of the time of writing this document. There's also the [VB-CABLE](https://vb-audio.com/Cable/index.htm) from Vincent Burel, but I've noticed that his software stutters sometimes while handling a lot of FMS in one session.

![](https://i.ibb.co/VJ05nQX/image.png)

The above settings allow you to have 2 channel, 16-bit and 48kHz quality sound. Notice that the SR is set to 48kHz. This is because Windows has a habit of playing with your sound settings after updates, so we lock it. I also recommend using [SoundSwitch](https://www.soundswitch.com/) as it shows you what input audio device you're using in the taskbar, so you can always know you're on the VAC.

**Note: Volume Control nor >= 4 channel doesn't work and makes your audio stutter.**

![](https://i.ibb.co/BVcTg6z/image.png)

The magic setting that emulates the sound over the VAC.

![](https://i.ibb.co/sFrvzHz/image.png)

An example setup of VAC running on SoundSwitch. To make this work, make sure your VACs are default.

# Further possible finetuning

After a Windows update/restart, your audio device will be selected to the Gamedac. To prevent this, you could create a script using [AudioDeviceCmdlets](https://github.com/frgnca/AudioDeviceCmdlets). Sadly, this project doesn't support the listen over device feature, as requested [here](https://github.com/frgnca/AudioDeviceCmdlets/issues/44). Luckily, [looped-back](https://github.com/HelloWorld017/looped-back) seems to support it so you'd have to make 2 scripts.

Another point to mention is that the microphone icon will always appear in the taskbar. This doesn't seem to happen in Windows 11, though. I have no idea to hide this.

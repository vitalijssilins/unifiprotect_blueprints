# UniFi Protect Home Assistant Blueprints

Below are some officially maintained blueprints for the UniFi Protect integration.

* [Forum Post with blueprints](https://community.home-assistant.io/t/unifi-protect-blueprints/362604)
* [UniFi Protect HA Integration](https://www.home-assistant.io/integrations/unifiprotect/)

## Requirements

To take full effect of this automation blueprint, your Home Assistant instance needs some setup beforehand.

* A UniFi Protect NVR running on a UDM Pro, UNVR or other Protect Console
* Home Assistant 2022.2.0 or newer running the [UniFi Protect integration](https://www.home-assistant.io/integrations/unifiprotect/)
* A UniFi camera pair with your NVR
  * (Smart/Motion Blueprint only): If you want to filter smart detections, you need a Smart Detection capable camera. This is any G4 series camera _except_ the EA G4 Instant.
  * (Doorbell Blueprint only): Your camera must have a chime (like the G4 Doorbell)
* (Smart/Motion/Doorbell Blueprints): A valid HTTPS certificate and public facing Home Assistant instance
  * If you do not have these, the actionable notifications and images will not appear in the notifications.
  * You do not need your _whole_ Home Assistant to be publically accessible. Only the paths `/api/camera_proxy/*` and `/api/webhook/*` need to be accessible outside of your network.
* (Optional, Doorbell Blueprint only): A `lock` entity for your door to allow you to unlock the door via notification
* (Smart/Motion Blueprint only, if you want HTML5 Push): [HTML5 Push notification Configured](https://www.home-assistant.io/integrations/html5)
* (Smart/Motion Blueprint only, if you want Mobile app): [HA Companion app](https://companion.home-assistant.io/) install on iOS or Android
* (Smart/Motion Blueprint only, if you want Telegram): The [Telegram integration](https://www.home-assistant.io/integrations/telegram) configured

## Doorbell Notifications

Receive notifications when someone rings your doorbell. Optional features:

* Actionable notification to unlock the door and play a TTS message
* Actionable notification to respond to the person at the door
* Actionable notification to mute further notifications for a configurable amount of time

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2FAngellusMortis%2Funifiprotect_blueprints%2Fmain%2Fblueprints%2Fautomation%2Funifiprotect%2Fpush_notification_doorbell_event.yaml)

## Motion / Smart Detection Notifications

Two blueprints here. Split out for performance (it is unlikely you will want both on the same notification target anyways!)

Receive notifications when motion or a smart detection event is trigger by one of your UniFi Protect cameras. Optional features:

* Filter for device tracker to "not be home" before triggering
* Filter for detected object (for smart detections)
* Actionable notification to mute further notifications for a configurable amount of time

### Motion Notifications

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2FAngellusMortis%2Funifiprotect_blueprints%2Fmain%2Fblueprints%2Fautomation%2Funifiprotect%2Fpush_notification_motion_event.yaml)

### Smart Detection Notifications

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FAngellusMortis%2Funifiprotect_blueprints%2Fblob%2Fmain%2Fblueprints%2Fautomation%2Funifiprotect%2Fpush_notification_smart_event.yaml)

## Dynamic Doorbell

Allows you to set your Doorbell text on your G4 Doorbell dynamically. Some examples include adding the current time and/or outside temp to your doorbell

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2FAngellusMortis%2Funifiprotect_blueprints%2Fmain%2Fblueprints%2Fautomation%2Funifiprotect%2Fdynamic_doorbell.yaml)

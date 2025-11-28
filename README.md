# Smart Home Safety Engine

A Home Assistant automation that combines door, motion, and light sensors to handle a few common safety/usefulness scenarios around the front door.

This automation covers three things:

1. **Arrival lighting at night**  
2. **Door-left-open reminders**  
3. **Unexpected entry alerts (Away / Asleep modes)**

---

## Features

- Turns on entrance lights automatically when you come home in the dark  
- Sends a notification if the door is left open  
- Optional camera recording on entry  
- Alerts if the door opens while you're Away or Asleep  
- Uses simple conditions and triggers so it’s easy to customise

---

## Requirements

You’ll need:

- Home Assistant
- A door sensor  
- A motion sensor in the entrance/hallway  
- A lux/light sensor (optional but recommended)  
- One or more entrance lights  
- (Optional) A camera at the door  
- A way to track “home mode” (e.g., an `input_select` for Home / Away / Asleep)
- Your phone’s notify service

Replace the example entity IDs in the YAML with your own.

---

## How it works

### 1. Arrival lighting (Home mode)

When the door opens at night and the entrance is dark:

- Turns on the entrance light  
- Optionally turns on a secondary light  
- (Optional) Starts camera recording  
- Keeps lights on while motion is active  
- Turns lights off after motion stops and the door closes

---

### 2. Door-left-open reminder

If the door has been open for a few minutes:

- Sends a notification  
- Optionally blinks a light  
- Sends a second notification if it’s still open later

---

### 3. Unexpected entry alert (Away / Asleep)

If the door opens while the house is in Away or Asleep mode:

- Turns on lights  
- Starts camera recording (if configured)  
- Sends a high-priority notification

---

## Automation overview

The logic uses:

- Multiple triggers (door open, open for X minutes, door closed)  
- `choose:` blocks for each scenario  
- Basic conditions for light levels, mode, and motion  
- Actions for lights, camera, and notifications  

It’s just a straightforward event-driven automation you can adjust for your own layout.

---

## Setup

1. Open `automation.yaml`.  
2. Replace the placeholder entity IDs with your own:  
   - `binary_sensor.DOOR_SENSOR`  
   - `binary_sensor.MOTION_SENSOR`  
   - `sensor.LIGHT_LEVEL`  
   - `light.ENTRANCE_LIGHT`  
   - `light.SECONDARY_LIGHT`  
   - `camera.ENTRY_CAMERA`  
   - `input_select.HOUSE_MODE`  
   - `notify.USER_PHONE`  
3. Paste the YAML into a new automation in Home Assistant (Edit in YAML).  
4. Adjust timings, lux thresholds, and brightness levels if needed.  
5. Test each part to make sure it works in your setup.

---

## Notes

This is just a single example automation.  
Feel free to fork it, change the timings, or split it into multiple automations depending on your home layout.

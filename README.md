# ha-sigenergy-card

![solar-card](https://github.com/user-attachments/assets/e986a16b-4170-42cc-bec2-7ad6de78afbf)

Based on the amazing work by [Rovin-Robin](https://github.com/Roving-Ronin) and others [here](https://github.com/TypQxQ/Sigenergy-Local-Modbus/discussions/184), this card mirrors the functionality (with numerous changes/fixes) but removes the house (that looks nothing like mine!).

## 1. Uses the [Sigenergy Local Modbus integration](https://github.com/TypQxQ/Sigenergy-Local-Modbus) default entities  
Plus two (that I remember) extras enabled:
- Sigen Plant > Controls > Remote EMS Control Mode
- Sigen Plant > Diagnostic > Rated Energy Capacity

## 2. Create a Template Sensor helper in Settings:

Name: **Sigen Plant Battery Usable Capacity**    (for entity_id sensor.sigen_plant_battery_usable_capacity)  
State:
```yaml
{{ (states('sensor.sigen_plant_battery_state_of_charge')|float(0) / 100 * states('sensor.sigen_inverter_rated_battery_capacity')|float(0))|round(2) }}
```  
Unit: kWh  
Device Class: Energy  
State Class: Total  
Device: (optional) Sigen Plant  

## 3. The Solar (PV) forecst may require a seperate integration 
I'm using [Solcast](https://github.com/BJReplay/ha-solcast-solar) - you'll likely need to modify this in the card.

## 4. Save/copy the images in *images* into your Home Assistant /config/www/  

## 5. In the UI, add a new *manual* card and paste the yaml from here  

</hr>

> [!NOTE]
> - Reminaing time (to charged/empty) only displays if time < 24 hours

Please let me know if something isn't working.

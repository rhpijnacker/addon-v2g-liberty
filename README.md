# V2G Liberty: optimised vehicle-to-grid charging of your EV

This integration lets you add full automatic and price optimized control over Vehicle to grid (V2G) charging. It has a 
practical local app in [HomeAssistant](https://www.home-assistant.io/) and uses the smart EMS [FlexMeasures](https://flexmeasures.io) for optimized schedules.

The schedules are optimized on day-ahead energy prices, so this works best with an electricity contract with dynamic (hourly) prices[^1].
We intend to add optimisation for your solar generation in the near future.

[^1]: For now: most Dutch energy suppliers are listed and all European energy prices (EPEX) are available for optimisation. There also is an option to upload your own prices, if you have an interest in this, please [contact us](https://v2g-liberty.eu/) to see what the options are.

![The V2G Liberty Dashboard](https://positive-design.nl/wp-content/uploads/2022/04/V2GL-1-1024x549.png)

You can read more about the project and its vision [here](https://v2g-liberty.eu/) and [here](https://seita.nl/project/v2ghome-living-lab/).

In practice, V2G Liberty does the following:
- In automatic mode: No worries, just plugin when you return home and let the system automatically optimize charging. 
- Set targets (e.g. be charged 100% at 7am tomorrow) which prompts FlexMeasures to update its schedules.
- Override the system and set charging to "Max Boost Now" mode in cases where you need as much battery SoC a possible quickly.

This integration is a Python app and uses:

- FlexMeasures for optimizing charging schedules. FlexMeasures is periodically asked to generate optimized charging schedules.
- Home Assistant for automating local control over your Wallbox Quasar. V2G Liberty translates this into set points which it sends to the Wallbox Quasar via modbus.
- The AppDaemon plugin for Home Assistant for running the Python app.

![V2G Liberty Architecture](https://user-images.githubusercontent.com/6270792/216368533-aa07dfa7-6e20-47cb-8778-aa2b8ba8b6e1.png)

---
title: Battery Level
sidebar_label: Battery Level
---

See the [battery level feature page](../features/battery.md) for more details on configuring a battery sensor.

See [Configuration Overview](index.md) for instructions on how to change these settings.

### Kconfig

Definition file: [zmk/app/Kconfig](https://github.com/zmkfirmware/zmk/blob/main/app/Kconfig)

| Config                               | Type | Description                                            | Default |
| ------------------------------------ | ---- | ------------------------------------------------------ | ------- |
| `CONFIG_ZMK_BATTERY_REPORTING`       | bool | Enables/disables all battery level detection/reporting | n       |
| `CONFIG_ZMK_BATTERY_REPORT_INTERVAL` | int  | Battery level report interval in seconds               | 60      |

:::note Default setting

While `CONFIG_ZMK_BATTERY_REPORTING` is disabled by default it is implied by `CONFIG_ZMK_BLE`, thus any board with BLE enabled will have this automatically enabled unless explicitly overriden.

:::

:::note BLE reporting on MacOS

On macOS the BLE battery reporting packets can cause the computer to wakeup from sleep. To prevent this, the battery _reporting_ service can be disabled by setting `CONFIG_BT_BAS=n`. This setting is independent of battery _monitoring_, for instance the battery level can still be indicated on a display.

:::

### Devicetree

Applies to: [`/chosen` node](https://docs.zephyrproject.org/latest/guides/dts/intro.html#aliases-and-chosen-nodes)

| Property      | Type | Description                                   |
| ------------- | ---- | --------------------------------------------- |
| `zmk,battery` | path | The node for the battery sensor driver to use |

## Battery Voltage Divider Sensor

Driver for reading the voltage of a battery using an ADC connected to a voltage divider.

### Devicetree

Applies to: `compatible = "zmk,battery-voltage-divider"`

See [Zephyr's voltage divider documentation](https://docs.zephyrproject.org/latest/build/dts/api/bindings/adc/voltage-divider.html).

## nRF VDDH Battery Sensor

Driver for reading the voltage of a battery using a Nordic nRF52's VDDH pin.

### Devicetree

Applies to: `compatible = "zmk,battery-nrf-vddh"`

Definition file: [zmk/app/module/dts/bindings/sensor/zmk,battery-nrf-vddh.yaml](https://github.com/zmkfirmware/zmk/blob/main/app/module/dts/bindings/sensor/zmk%2Cbattery-nrf-vddh.yaml)

This driver has no configuration.



VCU

- heartbeat check
- R2D state

MCC
- APPS
- BPPC
- R2D state


## VCU:

## Setups

<!-- |TIM13||
|:---|---:|
| Proposed $f$ | $ 125 \ Hz$
| Proposed $P$ | $ \dfrac{1}{125} = 0.008 \ sec = 8 \ ms $
| APB1 TIM | `250 MHz`
| Prescalar | `3125`
| Counter | `10000`
| Effective $f$ | $ \dfrac{250 * 10^6}{ 3125 * 10000 } = 8 $
--- -->
|TIM16||
|:---|---:|
| Proposed $f$ | $ 5 \ Hz$
| Proposed $P$ | $ \dfrac{1}{5} = 0.05 \ sec = 200 \ ms $
| APB2 TIM | `250 MHz`
| Prescalar | `5000`
| Counter | `10000`
| Effective $f$ | $ \dfrac{250 * 10^6}{ 5000 * 10000 } = 5 $
---
|TIM17||
|:---|---:|
| Proposed $f$ | $ 20 \ Hz$
| Proposed $P$ | $ \dfrac{1}{20} = 0.05 \ sec = 50 \ ms $
| APB2 TIM | `250 MHz`
| Prescalar | `1250`
| Counter | `10000`
| Effective $f$ | $ \dfrac{250 * 10^6}{ 1250 * 10000 } = 20 $
---
|FDCAN1||
|:---|---:|
| Proposed $f$  | $ 500000 \ Hz$ |
| Nominal Prescalar  | `10` |
| Nominal Time Seg 1  | `2` |
| Nominal Time Seg 2  | `2` |
|||
| Std Filters Nbr  | `1` |
| Ext Filters Nbr  | `0` |
| RX Fifo0 Elem Nbr  | `1` |
| RX Fifo0 Elem Size  | `16 Bytes` |
| RX Fifo1 Elem Nbr  | `0` |
| RX Fifo1 Elem Size  | `-` |
| RX Buffer Nbr  | `0` |
| RX Buffer Size  | `-` |
| TX Events Nbr  | `0` |
| TX Buffer Nbr  | `32` |
| TX Fifo Queue Elem Nbr  | `32` |
| TX Fifo Queue Mode  | `FIFO` |
| TX Elem Size  | `12 Bytes` |
|||
| Ram Offset  | `0` |
---
|FDCAN2||
|:---|---:|
| Proposed $f$  | $ 500000 \ Hz$ |
| Nominal Prescalar  | `10` |
| Nominal Time Seg 1  | `2` |
| Nominal Time Seg 2  | `2` |
|||
| Std Filters Nbr  | `1` |
| Ext Filters Nbr  | `0` |
| RX Fifo0 Elem Nbr  | `1` |
| RX Fifo0 Elem Size  | `16 Bytes` |
| RX Fifo1 Elem Nbr  | `0` |
| RX Fifo1 Elem Size  | `-` |
| RX Buffer Nbr  | `0` |
| RX Buffer Size  | `-` |
| TX Events Nbr  | `0` |
| TX Buffer Nbr  | `32` |
| TX Fifo Queue Elem Nbr  | `32` |
| TX Fifo Queue Mode  | `FIFO` |
| TX Elem Size  | `12 Bytes` |
|||
| Ram Offset  | `11` |
---
|FDCAN3||
|:---|---:|
| Proposed $f$  | $ 500000 \ Hz$ |
| Nominal Prescalar  | `10` |
| Nominal Time Seg 1  | `2` |
| Nominal Time Seg 2  | `2` |
|||
| Std Filters Nbr  | `1` |
| Ext Filters Nbr  | `0` |
| RX Fifo0 Elem Nbr  | `1` |
| RX Fifo0 Elem Size  | `16 Bytes` |
| RX Fifo1 Elem Nbr  | `0` |
| RX Fifo1 Elem Size  | `-` |
| RX Buffer Nbr  | `0` |
| RX Buffer Size  | `-` |
| TX Events Nbr  | `0` |
| TX Buffer Nbr  | `32` |
| TX Fifo Queue Elem Nbr  | `32` |
| TX Fifo Queue Mode  | `FIFO` |
| TX Elem Size  | `12 Bytes` |
|||
| Ram Offset  | `22` |


## Interrupts
|||
|:---|---:|
| TIM16 | `loop watchdog (task_app)` |
| TIM17 | `loop watchdog (task_heartbeatC)` |
| FDCAN | `Incoming FDCAN message` |


### FDCAN
1. Get Message + Get Which FDCAN Inst
2. Log rcv timing + Log sender + Log msg send id
3. Update machine state with msg content

### TIM
1. Get Which TIM Inst
2. if inst == TIM16: run task_app();
3. elif inst == TIM17: run task_heartbeatC()

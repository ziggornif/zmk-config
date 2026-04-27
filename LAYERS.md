# Lily58 — Layers

Documentation des layers définis dans `config/lily58.keymap`.

## Vue d'ensemble

| # | Nom | Rôle | Accès |
|---|---|---|---|
| 0 | `default_layer` | Frappe normale (QWERTY + homerow mods) | Layer de base |
| 1 | `lower_layer` | Touches F, gestion fenêtres, symboles | `mo 1` (pouce gauche) |
| 2 | `raise_layer` | Médias, navigation, flèches | `lt 2 TAB` (pouce gauche interne, hold) |
| 3 | `layer_3` | Caractères accentués FR | `lt 3 SPACE` (pouce droit interne, hold) **ou** combo `LOWER + TAB/RAISE` |
| 4 | `layer_4` | Bluetooth & alimentation | `lt 4 SPACE` (pouce droit, hold) |

## Cluster pouces (default)

```
Gauche                          Droite
┌──────┬──────┬──────┬──────┐  ┌──────┬──────┬──────┬──────┐
│ ALT  │ GUI  │LOWER │TAB / │  │SPACE │SPACE │ BSPC │ DEL  │
│      │      │(mo 1)│RAISE │  │ /L3  │ /L4  │      │      │
└──────┴──────┴──────┴──────┘  └──────┴──────┴──────┴──────┘
```

`TAB/RAISE` = `lt 2 TAB` : tap → TAB, hold → layer 2.
`SPACE/L3` = `lt 3 SPACE` : tap → SPACE, hold → layer 3.
`SPACE/L4` = `lt 4 SPACE` : tap → SPACE, hold → layer 4.

---

## Layer 0 — Default

```
┌─────┬─────┬─────┬─────┬─────┬─────┐                   ┌─────┬─────┬─────┬─────┬─────┬─────┐
│ ESC │  1  │  2  │  3  │  4  │  5  │                   │  6  │  7  │  8  │  9  │  0  │  `  │
├─────┼─────┼─────┼─────┼─────┼─────┤                   ├─────┼─────┼─────┼─────┼─────┼─────┤
│ TAB │  Q  │  W  │  E  │  R  │  T  │                   │  Y  │  U  │  I  │  O  │  P  │  -  │
├─────┼─────┼─────┼─────┼─────┼─────┤                   ├─────┼─────┼─────┼─────┼─────┼─────┤
│SHFT │  A  │  S  │  D  │  F  │  G  │                   │  H  │  J  │  K  │  L  │  ;  │  '  │
├─────┼─────┼─────┼─────┼─────┼─────┼─────┐       ┌─────┼─────┼─────┼─────┼─────┼─────┼─────┤
│CTRL │  Z  │  X  │  C  │  V  │  B  │  [  │       │ENTR │  N  │  M  │  ,  │  .  │  /  │  =  │
└─────┴─────┴─────┼─────┼─────┼─────┼─────┤       ├─────┼─────┼─────┼─────┼─────┴─────┴─────┘
                  │ ALT │ GUI │ L1  │ TAB │       │SPC  │SPC  │BSPC │ DEL │
                  │     │     │     │ /L2 │       │ /L3 │ /L4 │     │     │
                  └─────┴─────┴─────┴─────┘       └─────┴─────┴─────┴─────┘
```

**Homerow mods** (rangée du milieu, hold = mod, tap = lettre) :

| Doigt | Gauche | Droite |
|---|---|---|
| Pinky | A → `LGUI` | `;` → `RGUI` |
| Annulaire | S → `LALT` | L → `RALT` |
| Majeur | D → `LSHIFT` | K → `RSHIFT` |
| Index | F → `LCTRL` | J → `RCTRL` |

Implémentés via les comportements custom `&hml` / `&hmr` (flavor `balanced`, ne déclenchent que sur la main opposée).

**Encodeur** : `VOL_UP / VOL_DN`.

---

## Layer 1 — Lower

Accès : maintenir `LOWER` (pouce gauche, position centrale).

```
┌─────┬─────┬─────┬─────┬─────┬─────┐                   ┌─────┬─────┬─────┬─────┬─────┬─────┐
│     │     │     │     │     │     │                   │     │     │     │     │ S+PS│PRTSC│
├─────┼─────┼─────┼─────┼─────┼─────┤                   ├─────┼─────┼─────┼─────┼─────┼─────┤
│ F1  │ F2  │ F3  │ F4  │ F5  │ F6  │                   │     │     │     │     │     │BSPC │
├─────┼─────┼─────┼─────┼─────┼─────┤                   ├─────┼─────┼─────┼─────┼─────┼─────┤
│ F7  │ F8  │ F9  │ F10 │ F11 │ F12 │                   │LHALF│LSCRN│RSCRN│RHALF│     │     │
├─────┼─────┼─────┼─────┼─────┼─────┼─────┐       ┌─────┼─────┼─────┼─────┼─────┼─────┼─────┤
│     │     │     │     │     │     │     │       │     │     │  -  │  +  │  {  │  }  │  |  │
└─────┴─────┴─────┴─────┴─────┴─────┴─────┘       └─────┴─────┴─────┴─────┴─────┴─────┴─────┘
```

**Macros gestion de fenêtres** (raccourcis OS, mappés sur GUI+ALT / GUI+ALT+CTRL) :

- `LHALF` → moitié gauche de l'écran courant
- `RHALF` → moitié droite de l'écran courant
- `LSCRN` → écran de gauche
- `RSCRN` → écran de droite

Sur la dernière rangée droite : symboles math/programmation `- + { } |`.

---

## Layer 2 — Raise

Accès : maintenir `TAB/RAISE` (pouce gauche interne).

```
┌─────┬─────┬─────┬─────┬─────┬─────┐                   ┌─────┬─────┬─────┬─────┬─────┬─────┐
│     │BRI- │BRI+ │PREV │PLAY │NEXT │                   │     │     │     │     │     │     │
├─────┼─────┼─────┼─────┼─────┼─────┤                   ├─────┼─────┼─────┼─────┼─────┼─────┤
│     │     │     │MUTE │VOL- │VOL+ │                   │HOME │PGDN │PGUP │ END │     │ERASE│
├─────┼─────┼─────┼─────┼─────┼─────┤                   ├─────┼─────┼─────┼─────┼─────┼─────┤
│SHFT │     │     │     │FSCRN│     │                   │  ←  │  ↓  │  ↑  │  →  │     │     │
├─────┼─────┼─────┼─────┼─────┼─────┼─────┐       ┌─────┼─────┼─────┼─────┼─────┼─────┼─────┤
│     │     │     │     │     │     │     │       │     │     │     │     │  [  │  ]  │  \  │
└─────┴─────┴─────┴─────┴─────┴─────┴─────┘       └─────┴─────┴─────┴─────┴─────┴─────┴─────┘
```

- `SHFT` (pinky gauche) : `&kt` (key-toggle) → bascule shift verrouillé.
- `FSCRN` : macro plein écran (GUI+ALT+F).
- `ERASE` : macro `eraseword` (Ctrl+Backspace).
- Cluster directionnel HJKL côté droit pour les flèches.

---

## Layer 3 — Accents français

Accès : maintenir `SPACE/L3` (pouce droit interne) **ou** combo `LOWER + TAB/RAISE` (positions 52 + 53).

```
┌─────┬─────┬─────┬─────┬─────┬─────┐                   ┌─────┬─────┬─────┬─────┬─────┬─────┐
│     │     │     │     │     │     │                   │     │     │     │     │     │     │
├─────┼─────┼─────┼─────┼─────┼─────┤                   ├─────┼─────┼─────┼─────┼─────┼─────┤
│     │     │     │  é  │     │     │                   │     │  ù  │  î  │  ô  │     │     │
├─────┼─────┼─────┼─────┼─────┼─────┤                   ├─────┼─────┼─────┼─────┼─────┼─────┤
│     │  à  │     │     │     │     │                   │     │  ü  │  ï  │  ë  │     │     │
├─────┼─────┼─────┼─────┼─────┼─────┼─────┐       ┌─────┼─────┼─────┼─────┼─────┼─────┼─────┤
│     │     │     │  ç  │  â  │  ê  │     │       │     │  û  │  è  │     │     │     │     │
└─────┴─────┴─────┴─────┴─────┴─────┴─────┘       └─────┴─────┴─────┴─────┴─────┴─────┴─────┘
```

Toutes les lettres accentuées passent par des **macros dead-key** qui supposent un layout système **US International** :

- `à è ù` → dead grave (`` ` ``) + lettre
- `é` → dead acute (`'`) + lettre
- `â ê î ô û` → dead circumflex (`Shift+6`) + lettre
- `ë ï ü` → dead diaeresis (`Shift+'`) + lettre
- `ç` → `'` + `c`

> Si le layout système n'est pas US Intl, ces macros produiront des séquences incorrectes.

---

## Layer 4 — Bluetooth & alimentation

Accès : maintenir `SPACE/L4` (pouce droit externe).

```
┌─────┬─────┬─────┬─────┬─────┬─────┐                   ┌─────┬─────┬─────┬─────┬─────┬─────┐
│     │     │     │     │     │     │                   │     │     │     │     │     │     │
├─────┼─────┼─────┼─────┼─────┼─────┤                   ├─────┼─────┼─────┼─────┼─────┼─────┤
│     │     │     │     │     │     │                   │BTCLR│ BT0 │ BT1 │ BT2 │     │     │
├─────┼─────┼─────┼─────┼─────┼─────┤                   ├─────┼─────┼─────┼─────┼─────┼─────┤
│     │     │     │     │     │     │                   │EP_ON│EP_OF│EP_TG│     │     │     │
├─────┼─────┼─────┼─────┼─────┼─────┼─────┐       ┌─────┼─────┼─────┼─────┼─────┼─────┼─────┤
│     │     │     │     │     │     │     │       │     │     │     │     │     │     │     │
└─────┴─────┴─────┴─────┴─────┴─────┴─────┘       └─────┴─────┴─────┴─────┴─────┴─────┴─────┘
```

- `BTCLR` : efface l'appairage Bluetooth courant.
- `BT0 / BT1 / BT2` : sélectionne un profil Bluetooth.
- `EP_ON / EP_OFF / EP_TG` : alimentation périphériques (ex. OLED).

---

## Comportements custom

| Label | Type | Usage |
|---|---|---|
| `&hml` | `hold-tap` | Homerow mods côté gauche, déclenchement main droite uniquement |
| `&hmr` | `hold-tap` | Homerow mods côté droit, déclenchement main gauche uniquement |

Paramètres : `flavor = "balanced"`, `tapping-term-ms = 280`, `quick-tap-ms = 175`, `require-prior-idle-ms = 150`, `hold-trigger-on-release`.

## Combos

| Touches (positions) | Action |
|---|---|
| `52` + `53` (les deux pouces gauches internes) | Active layer 3 (`mo 3`) |

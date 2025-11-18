# Spire Climber - Roguelike Game Design Guidelines

## Design Approach
**Reference-Based Approach**: Drawing inspiration from Slay the Spire's dark fantasy aesthetic combined with modern roguelike games (Hades, Darkest Dungeon). The design emphasizes atmospheric depth, clear information hierarchy, and tactile, satisfying interactions.

## Core Design Principles
1. **Dark Fantasy Atmosphere**: Moody, mysterious ambiance with strategic use of glowing accents
2. **Information Clarity**: All stats, damage ranges, and game state must be immediately readable
3. **Tactical Focus**: UI supports strategic decision-making without visual clutter
4. **Progressive Revelation**: UI elements animate in/out smoothly to maintain immersion

---

## Typography System

**Primary Font**: 'Cinzel' (Google Fonts) - Medieval fantasy serif for headings, titles, class names
**Secondary Font**: 'Roboto Condensed' - Clean, readable sans-serif for stats, numbers, descriptions
**Monospace Font**: 'JetBrains Mono' - For damage calculations, numeric displays

**Hierarchy**:
- Game Title/Section Headers: Cinzel, 2.5rem, font-weight 700, letter-spacing 0.05em
- Class Names/Item Names: Cinzel, 1.5rem, font-weight 600
- Body Text/Descriptions: Roboto Condensed, 1rem, font-weight 400
- Stats/Numbers: JetBrains Mono, 1.125rem, font-weight 500
- Small Labels: Roboto Condensed, 0.875rem, font-weight 400, uppercase, letter-spacing 0.1em

---

## Layout & Spacing

**Spacing Scale**: Use Tailwind units of 1, 2, 3, 4, 6, 8, 12, 16 for consistent rhythm
- Component padding: p-4 to p-6
- Section gaps: gap-6 to gap-8
- Card spacing: space-y-4
- Button padding: px-6 py-3

**Grid System**:
- Combat view: 2-column split (map/stats left, combat right) on desktop
- Inventory: 4-5 column grid for items
- Spell grid: 2-3 columns for spell cards
- Mobile: Single column stack with priority given to active content

---

## Component Library

### Game Screens

**1. Class Selection Screen**
- Full-screen overlay with centered 3-card layout
- Each class card: Large emoji icon, class name, stat preview, starter equipment list
- Cards have subtle glow on hover, scale transform
- "Choose Easy Mode" toggle below cards with clear explanation
- Name input field appears after class selection with fantasy-styled input border

**2. Main Game View (Map + Stats)**
- Left sidebar (30% width): Vertical spire map visualization
  - Animated path connections between nodes
  - Emoji icons for encounters in circular containers
  - Player position highlighted with pulsing glow
  - Crown at top with divine radiance effect
  - Visited nodes marked with translucent 'X'
- Right sidebar (20% width): Player stats panel
  - HP bar with current/max values
  - Mana bar with current/max values  
  - Damage range display
  - Coin counter with coin icon
  - Compact equipped items preview
- Center (50%): Command menu or active encounter content

**3. Combat Interface**
- Enemy card: Large portrait area, HP bar, intent indicator (attack/defend icon + value)
- Player action area: Spell cards in hand-like spread
- Each spell card shows: Name, mana cost (crystal icon), effect preview
- Attack button triggers damage calculation with animated number pop-ups
- Turn counter and mana regeneration indicator

**4. Inventory Screen**
- Grid layout for all items (weapons, armor, amulets)
- Each item card: Icon placeholder, item name, stat bonus, equipped indicator
- Filter tabs: All / Weapons / Armor / Amulets
- "Equip" button appears on hover/click
- Currently equipped items have gold border glow

**5. Shop Interface**
- Merchant header with greeting text
- Item cards in 3-column grid
- Each card shows: Item, stats, cost (coin icon + number)
- "Purchase" button (disabled if insufficient coins)
- Exit shop button

**6. Chest Encounter**
- Animated chest opening sequence
- Reward reveal with glowing item card
- "Take Item" button adds to inventory

### UI Elements

**Buttons**:
- Primary actions: Large, glowing border, uppercase text
- Secondary actions: Subtle border, normal case
- Disabled state: Reduced opacity, no glow
- Icon buttons for compact actions (info, close, etc.)

**Progress Bars** (HP/Mana):
- Segmented bar design with current/max text overlay
- HP: Red gradient fill
- Mana: Blue/cyan gradient fill
- Smooth transition animations on value changes

**Cards** (Items/Spells/Enemies):
- Rounded corners (rounded-lg)
- Border with subtle glow for rarity/type
- Shadow depth for elevation (shadow-lg)
- Hover: Slight lift (translate-y-1) with increased glow

**Modal Overlays**:
- Dark backdrop (bg-black/80)
- Centered content with border frame
- Close button (X icon) in top-right
- Escape key to dismiss

---

## Iconography

**Icons**: Use Heroicons (outline style for UI, solid for filled states)
- Combat: Sword, shield, sparkles (spell), heart (heal)
- Inventory: Backpack, shopping bag, gift box
- Stats: Heart (HP), droplet (mana), flame (damage), coins
- Navigation: Arrows, chevrons, X for close

**Emoji Integration**: Preserve original emoji for classes and encounters
- 🤺 Knight, 🧙 Mage, 🤴 Gambler
- 💰 Shop, 🎁 Chest, ❓ Random, 🗡️ Fight, 👑 Crown
- Display at appropriate sizes (text-4xl to text-6xl for prominence)

---

## Animations & Effects

**Sparingly Applied**:
- Page transitions: Fade in/out (300ms)
- Combat damage: Number pop-ups with scale + fade
- Card reveals: Flip animation for chest rewards
- Spell casting: Brief particle burst (CSS animation)
- Victory/defeat: Screen flash + modal entrance

**NO Animations**:
- Background parallax scrolling
- Continuous floating/bobbing elements
- Auto-playing effects
- Excessive glow pulsing

---

## Images

**Hero Section**: NOT APPLICABLE - This is a game UI, not a marketing site

**In-Game Images**:
- Character portraits: Placeholder silhouettes for Knight/Mage/Gambler (described as "medieval knight silhouette", "wizard with staff", "regal figure with crown")
- Enemy portraits: Generic fantasy creatures (goblin, skeleton, dragon) as described placeholders
- Background textures: Subtle stone/parchment patterns for panels (CSS background images, low opacity)
- Boss fight: Dramatic portrait for final encounter

---

## Accessibility

- High contrast text on all backgrounds (WCAG AA minimum)
- Keyboard navigation: Tab through buttons, Enter to select, Escape to close modals
- Screen reader labels on all interactive elements
- Focus indicators on all focusable elements (ring-2 ring-offset-2)
- Text remains readable at 200% zoom

---

## Responsive Behavior

**Desktop (1024px+)**: Full 3-panel layout (map | content | stats)
**Tablet (768px-1023px)**: 2-panel (combined map+stats sidebar | main content)
**Mobile (<768px)**: Single column, collapsible map drawer, stats in compact header bar
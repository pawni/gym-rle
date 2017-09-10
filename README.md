# gym-rle

The [Retro Learning Environment](https://github.com/nadavbh12/Retro-Learning-Environment) supports SNES (Super Nintendo Entertainment System) video games such as Mario and Mortal Kombat.

# Installation

```bash
cd gym-rle
pip install -e .
```

Roms for the available games need to put in the gym/envs/rle/roms dir with lowercase separated names (e.g. mortal_kombat.sfc).
You can see the list of supported games in `gym_rle/__init__.py` .

# Getting started with Pokemon

You have to get a Pokemon Red or Blue rom (yes, you have a cartridge at home and make a copy yourself ... )
Then you can use the following code for playing around in jupyter.
```
import matplotlib.pyplot as plt
from IPython import display

import gym
import gym_rle
import time

def render(env):
    img = env._get_image()
    plt.imshow(img)
    plt.show()

env = gym.make('Pokemon-v0')
env.reset()

def noop():
    for _ in range(100):
        act(8, False)
    act(8)
    
total_reward = 0
def act(action, plot=True):
    global total_reward
    observation, reward, done, info = env.step(action)
    total_reward += reward
    if plot:
        plt.imshow(observation)
        plt.show()

        print('rew {} tot {}'.format(reward, total_reward))

# 0 select
# 1 start
# 2 b
# 3 a
# 4 right
# 5 left
# 6 down
# 7 up
# 8 noop
act(8)
```

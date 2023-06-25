# Incongruity-Aware Crossmodal Transformer with Adaptive Conflict Elimination
For AAAI

The project I am currently focusing on is to propose a new paradigm for multimodal fusion.
      
[1] In the current multimodal learning, there is a situation where the learning processes of different modalities in the neural network are inconsistent, that is, the advantageous modality converges faster and leads to the convergence of the entire model, which makes the model unable to fully explore the potential information of the inferior modalities. The current related advanced work is the OGM [https://github.com/GeWu-Lab/OGM-GE_CVPR2022] method from Renmin University of China, which modulates the gradient of each single modalities during the model learning process to make the modalities learning progresses level off. 

[2] In the experiment, I found that in some data sets, such as MOSI & MOSEI and IEMOCAP, the former (MOSI, MOSEI) are the data obtained from Youtube, which may contain lots of noisy information; and the latter is the data created by the laboratory, which is cleaner than the former. OGM has a bad effect on the former and even has a negative impact, while the effect on IEMOCAP is better and significant.

[3] We guess that OGM only considers the modulation of the gradient modulus length, and does not consider the possible conflicts of the gradient optimization directions of different modalities, that is, the labels corresponding to different modalities may be inconsistent. In multi-task learning, gradient surgery can solve similar target optimization conflict problems, but in the multimodal Transformer structure, each modality has a separate encoder(s), so gradient surgery is not worked here (as encoders cannot share their parameters).

[4] We propose a new multimodal fusion paradigm (primary-auxiliary) to solve the problem of multimodal conflict (inter-modal incongruity). Its main goal is to establish the most robust modality as the primary modality based on relevant metrics (such as KL-div) to lead the overall model optimization direction, and other modalities provide auxiliary information for the primary modality. The advantage of this architecture is that it provides robust learning to decrease the negative impact for the overall model due to any presence of noise in multiple modalities.

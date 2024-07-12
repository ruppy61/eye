瞼や瞳孔を検出するプログラムを作りました。
VScodeを用いてWindowsで作成しました。
モルフォジ演算をもちいて黒っぽい部分を消してよりはっきり見えるようにしました。
また私の動作環境がWindowなためファイルの/がひとつだけだとエラーが発生してしまうため/を２つほど書いています。Macでの動作テストをしていないためなるべくWindowsでの実行をお願いします。

import numpy as np
import cv2

for i in range(10):
    if __name__=='__main__':
     src=cv2.imread(".//images//cl//cl0000{}.png".format(i))
     gray=cv2.cvtColor(src,cv2.COLOR_BGR2GRAY)
     ret,img=cv2.threshold(gray,127,255,cv2.THRESH_OTSU)

     kernel=np.ones((5,5),np.uint8)
     img_dilation=cv2.dilate(img,kernel,iterations=1)
     cv2.imshow('Dilation',img_dilation)

     cv2.imwrite('.//img//dilation.png',img_dilation)
     cv2.waitKey(0)
    
